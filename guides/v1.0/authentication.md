# Authentication

The following steps show how your application interacts with the Edlink API to obtain a user's consent to perform API requests on their behalf. Your application must have that consent before it can execute any API requests that require user authentication (i.e. any requests in the User API section of this documentation). 

Edlink implements the standard OAuth 2.0 authorization process. If you have already implemented OAuth 2.0 for other services (e.g. Sign in with Google), this flow should be familiar, and you may be able to benefit from reusing some existing code.

Here is a quick summary of the steps:

1. Your server directs the user to Edlink so they can authenticate with the provider linked by their admin.
2. The user authenticates with their provider and is redirected to Edlink.
3. The user is redirected to your application's redirect URI, along with an authorization code.
4. Your server exchanges the code with the Edlink server and receives a bearer token and a refresh token.
5. Your server can now make requests on the user's behalf.

## 1. Set Authorization Parameters

Your first step is to create the authorization request. This basically means that you are going to construct a URL and then redirect your users to that URL when they click the SSO link on your application. The URL contains parameters that identify your application and tells us what to do after the user has authenticated. The Edlink OAuth 2.0 endpoint is located at `https://ed.link/sso/login`. As with all of our endpoints, this endpoint is only accessible over HTTPS. It is also highly encouraged that you supply a `state` string in addition to the other details required.

You will want to redirect your users to the following URL, with the blanks filled in with your application's details:

`https://ed.link/sso/login?client_id=[...]&redirect_uri=[...]&state=[...]&response_type=code`

In the event that the user launches from their SSO provider (e.g. Clever, Classlink) into your application, some of the standard parameters will not be available. In particular, there will be no `state` variable specified because the launch request did not originate from your application. In this case, Edlink will select the *first* specified `redirect_uri` (what we call your "primary" redirect_uri) and send the user to that location.

This means that you should be mindful of the order in which you specify your application's redirect URIs. It is **not** recommended that you place development URIs in the first position. Instead, make sure your production URI is located first so users are redirected successfully. If you need to test a development URI, we recommend that you create a second Edlink `application` for this purpose. You will receive new API keys and you will be able to specify a *second* set of application redirect URIs.

## 2. Edlink Prompts the User to Authenticate

At this stage, Edlink displays an authorization window that guides them through the authorization process. This is handled by first: determining which authentication provider has been specified by the school administrator; then, directing the user to that provider (e.g. Canvas). When the user has completed the authentication process with their provider, they are redirected back to Edlink. Your application doesn't need to do anything at this stage.

## 3. Edlink Sends the User to Your Redirect URI

Edlink then forwards the user back to your application using the `redirect_uri` specified in the initial SSO request (Step 1). If the user successfully authenticated, then the request will also contain an authorization code. If the user did not authenticate successfully, or if they declined access, the response will an error message.

In the event that the user launches from their SSO provider (e.g. Clever, Classlink) into your application, there will be no `state` variable specified. In addition, Edlink will select the *first* specified `redirect_uri` (what we call your "primary" redirect_uri) and send the user to that location.

#### A Successful Response URL

`https://yoursite.com?state=f329q8nf0lblmkn439&code=m2p4309fp9dc1mk23`

#### An Error Response URL

`https://yoursite.com?state=f329q8nf0lblmkn439&error=declined_authorization`

## 5. Exchange the Code for Access and Refresh Tokens

After your redirect URL receives the code, your server can exchange the code for an access token and refresh token by sending a `POST` request to the Edlink server. The purpose of this step is to ensure that our user redirect was sent to the correct location, and that it was not intercepted or modified by anyone else in transit. The way we confirm this, is by looking at the authorization code that you send back to us, in conjunction with your application's secret key.

> This exchange **cannot happen on the client side**. This would expose your secret key and constitute a massive breach of security for yourself and your clients.
>
> For more information, please review [our guide regarding security](security).

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

# Using the Bearer Token

After retrieving an access token you can use it to make requests on the user's behalf. To make a request with the access token, simply add an `Authorization` header to the request containing a string containing the word `Bearer` followed by a space and the `access_token`.

```javascript
const user = await axios.get('https://ed.link/api/v1/my/profile', {
    headers: {
        'Authorization': `Bearer ${access_token}`
    }
});
```

## Refreshing the Bearer Token

Bearer tokens expire after 3600 seconds (1 hour), as defined by the `expires_in` field returned during Step 5. After the one hour period has expired, any requests made using the token will result in a `401 Unauthorized` error. You may wish to refresh a user's bearer token to continue making requests on their behalf.

To refresh a bearer token, you must save the `refresh_token` that was granted to you in Step 5. This token must be stored securely, as compromised refresh tokens can result in a breach of user data. Making another request to the OAuth endpoint from Step 5 (with some slightly different parameters) will grant you a new token.

> This exchange **cannot happen on the client side**. This would expose your secret key and constitute a massive breach of security for yourself and your clients.
>
> For more information, please review [our guide regarding security](security).

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
