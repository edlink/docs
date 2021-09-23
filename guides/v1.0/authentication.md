# Authentication

This page is not a guide to authentication (that can instead be found [here](/docs/guides/v1.0/user-authentication)). Instead, it will just be a summary of the available endpoints for authentication. If you have experience with writing OAuth 2.0 connections, these endpoints (and this entire process) should be very familiar to you.

## Construct a Login URL

`https://ed.link/sso/login?client_id=[...]&redirect_uri=[...]&state=[...]&response_type=code`

## Receive an Authorization Code

In the event the user signs in successfully (or selects one of their previously accessed accounts), Edlink will redirect them to the Redirect URI specified in your login URL. In addition, Edlink will supply up to two parameters:

* `code` The OAuth 2.0 authorization code that we will expect to receive further down this page.
* `state` If you specified a state variable in your Login URL (above), then Edlink will pass this back to you.

`https://yoursite.com?state=f329q8nf0lblmkn439&code=m2p4309fp9dc1mk23`

## Receiving an Error Code

Sometimes the user is not successful during the login process. This can happen for many reasons such as:

* They intentionally cancel their sign in.
* They reject the permissions that Edlink asks for.
* Their SSO provider is not available / offline.

In this event, Edlink will redirect users to the Redirect URI specified in your Login URL. In addition, Edlink will attach the `state` specified in your Login URL and *may* attach an `error` query parameters with more specific details about why the login attempt was not successful.

`https://yoursite.com?state=f329q8nf0lblmkn439&error=declined_authorization`

## Exchange the Code for Access and Refresh Tokens

After your redirect URL receives the code, your server can exchange the code for an access token and refresh token by sending a `POST` request to the Edlink server. The purpose of this step is to ensure that our user redirect was sent to the correct location, and that it was not intercepted or modified by anyone else in transit. The way we confirm this, is by looking at the authorization code that you send back to us, in conjunction with your application's secret key. This exchange **cannot happen on the client side**. This would expose your secret key and constitute a massive breach of security for yourself and your clients.

Please note: the request body must be of type `application/json`.

#### Sample Token Exchange Request
```javascript
const request = {
    code: '<authorization code from initial request>',
    client_id: '<your application id>',
    client_secret: '<your application secret>',
    redirect_uri: '<the redirect URI that you used above>',
    grant_type: 'authorization_code'
};

const response = await axios.post('https://ed.link/api/authentication/token', request);
```

#### Sample Token Exchange Response
```json
{
    "$data": {
        "access_token": "6j42gte2lk1n29nte2lqmkk42g1n28nf0lbl9q",
        "refresh_token": "av439q8nlbl0l4309fp39q8nf0mkn43943f09f",
        "expires_in": 3600
    }
}
```

## Refreshing the Bearer Token

Bearer tokens expire after 3600 seconds (1 hour), as defined by the `expires_in` field returned during Step 5. After the one hour period has expired, any requests made using the token will result in a `401 Unauthorized` error. You may wish to refresh a user's bearer token to continue making requests on their behalf.

To refresh a bearer token, you must save the `refresh_token` that was granted to you in Step 5. This token must be stored securely, as compromised refresh tokens can result in a breach of user data. Making another request to the OAuth endpoint from Step 5 (with some slightly different parameters) will grant you a new token. This exchange **cannot happen on the client side**. This would expose your secret key and constitute a massive breach of security for yourself and your clients.

Please note: the request body must be of type `application/json`.

#### Sample Token Refresh Request
```javascript
const request = {
    client_id: '<your application id>',
    client_secret: '<your application secret>',
    grant_type: 'refresh_token',
    refresh_token: '<a valid refresh token>'
};

const response = await axios.post('https://ed.link/api/authentication/token', request);
```

#### Sample Token Refresh Response
```json
{
    "$data": {
        "access_token": "6j42gte2lk1n29nte2lqmkk42g1n28nf0lbl9q",
        "refresh_token": "av439q8nlbl0l4309fp39q8nf0mkn43943f09f",
        "expires_in": 3600
    }
}
```