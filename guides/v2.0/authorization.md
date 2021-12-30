# Authorization

Accessing the Edlink API requires your secret key, which is available after you create an application in the dashboard.
Your secret key acts as a bearer token and conveys your identity to Edlink.

All requests must be made over HTTPS to avoid exposing the key to the public. We will redirect or reject all requests
not made via HTTPS.

## Graph API Authorization

Your application's secret key can be used to [retrieve a list of active integrations](../../api/v1.0/graph/integrations).
This list contains all the different individual school data sources that have connected to your application.

When school administrators grant access to their data source (e.g. Canvas), a new integration will appear on the list.
When they revoke access, it will be removed. Each integration contains its own access token that you will use to access
the Graph API. This access token is sent in the same fashion as your application's token.

### Making Requests

To make a request to a protected endpoint - which is virtually all endpoints - you must include your secret key in an
HTTP header called `Authorization`. Edlink uses this header to identify incoming requests. Set the `Authorization`
header to a value of the word `Bearer`, followed by a single space, followed by your key.

```javascript
// Load the classes for the integration associated with the specified key.
const classes = await axios.get('https://ed.link/api/v2/graph/classes', {
	headers: {
		'Authorization': 'Bearer XxYUqqrxHBo6yWBqcry8b73GhibnrQyq'
	}
});
```

## User API Authorization

If you have experience writing OAuth 2.0 connections, these endpoints (and this entire process) should be very familiar
to you.

### 1. Construct a Login URL

In order to begin the process of obtaining an authorization code, we must construct a login URL for the user.

```
https://ed.link/sso/login
?client_id=[...]
&redirect_uri=[...]
&state=[...]
&response_type=code
```

| Parameter | Description |
|---|---|
| `client_id` | This should be set to the **Application ID** listed in the **Application Keys** section of your application configuration. 
| `redirect_uri` | This is where we'll send users after a login attempt. This URI must be explicitly specified in your application settings, or we won't allow it. 
| `state` | While not required, it's good practice to set a random variable here and check that it's the same in the next step.

### 2. Receiving a Response from Edlink

Next, we'll see how to process the response received from Edlink after a user signs in or fails to sign in.

#### Receiving an Authorization Code

In the event the user signs in successfully (or selects one of their previously accessed accounts), Edlink will redirect
them to the `redirect_uri` you specified previously with some additional parameters attached.

```
https://yoursite.com/
?state=f329q8nf0lblmkn439
&code=m2p4309fp9dc1mk23
```

| Parameter | Description |
|---|---|
| `state` | If you specified a state variable in your login URL, then Edlink will pass this back to you. It's good practice to make sure that this variable did not change since the previous step. |
| `code` | This is your user's authorization code. You'll need this code for the next step. |

#### Receiving an Error Code

Sometimes the user is not successful during the login process. This can happen for many reasons, but most commonly:

* They intentionally cancelled the sign-in process.
* They rejected the permissions that Edlink asked for.
* Their SSO provider is not available / offline.

In this event, Edlink will redirect users to the `redirect_uri` specified previously.

```
https://yoursite.com
?state=f329q8nf0lblmkn439
&error=declined_authorization
```

| Parameter | Description |
|---|---|
| `state` | If you specified a state variable in your login URL, then Edlink will pass this back to you. It's good practice to make sure that this variable did not change since the previous step. |
| `error` | If we know what went wrong, we'll provide more specific details here about why the login attempt was unsuccessful. |

### 3. Getting an Access Token

After your redirect URL receives the code, your server can exchange the code for an access token and refresh token by
sending a `POST` request to Edlink.

The purpose of this step is to ensure that our user redirect was sent to the correct location, and that it was not
intercepted or modified by anyone else in transit.

The way we confirm this is by validating the authorization code that you send back to us in conjunction with your
application's secret key.

> **This exchange should NEVER happen on the client side.** You should make this request on your server side or backend in a secure environment. The client's web browser should **never** see your `client_secret`. This would constitute a massive breach of security for yourself and your clients.
>
> For more information, please review [our guide regarding security](security).

#### Sample Token Exchange Request

| Field | Description |
| --- | --- |
| `code` | This should be set to the authorization code you received in step 2. |
| `client_id` | This should be set to the **Application ID** listed in the **Application Keys** section of your application configuration. |
| `client_secret` | This should be set to the **Secret Key** listed in the **Application Keys** section of your application configuration. |
| `redirect_uri` | This should be set to the `redirect_uri` you used in step 1. |
| `grant_type` | This should be set to `authorization_code`. |

The request body must be of type `application/json`.

```javascript
// Replace the ellipses with the appropriate 
// values from the table above.
const request = {
	code: '...',
	client_id: '...',
	client_secret: '...',
	redirect_uri: '...',
	grant_type: 'authorization_code'
};

const response = await axios.post('https://ed.link/api/authentication/token', request);
```

#### Sample Token Exchange Response

Assuming all goes well with your request, you'll get a response that looks something like this.

```json
{
  "$data": {
    "access_token": "6j42gte2lk1n29nte2lqmkk42g1n28nf0lbl9q",
    "refresh_token": "av439q8nlbl0l4309fp39q8nf0mkn43943f09f",
    "expires_in": 3600
  }
}
```

The `access_token` retrieved from this endpoint can be used in step 4 to make requests. It `expires_in` 3600 seconds (1 hour) as indicated. After the expiration, any requests made will result in a `401 Unauthorized` error.

You should securely store the `access_token` to use for any requests you want to make on behalf of this user for the next hour. **This token should never be exposed to the user.**

You should securely store the `refresh_token` so it can be used to obtain a new `access_token` after it expires. You can follow the instructions in step 5 to get a new `access_token`. **This token should never be exposed to the user.**

> **These access and refresh tokens are very sensitive info.** You should ensure that they are kept on the server side or backend of your application in a secure environment. Compromised access or refresh tokens can result in a breach of user data.
>
> For more information, please review [our guide regarding security](security).

### 4. Making Requests

To make a request to a protected endpoint - which is virtually all endpoints - you must include the
user's `access_token` in an HTTP header called `Authorization`. Edlink uses this header to identify incoming requests.
Set the `Authorization` header to a value of the word `Bearer`, followed by a single space, followed by
the `access_token`.

```javascript
// Fetch the current user's profile.
const profile = await axios.get('https://ed.link/api/v2/my/profile', {
	headers: {
		'Authorization': 'Bearer GhibYUqqrxHBo6yWBqnrQXxcry8b73yq'
	}
});
```

At this stage, you can use your valid `access_token` to make requests to any endpoint in the User API. This token is not valid for the Graph API.

### 5. Refreshing the Access Token

As explained in step 3, no `access_token` is valid forever. They'll expire after an hour. You may wish to get a new `access_token` to continue making requests on their behalf.

This is where the `refresh_token` you saved earlier comes in.

We can make another request to the `/authentication/token` endpoint with slightly different parameters to get a new, updated `access_token`. 

#### Sample Token Refresh Request

| Field | Description |
| --- | --- |
| `client_id` | This should be set to the **Application ID** listed in the **Application
Keys** section of your application configuration. |
| `client_secret` | This should be set to the **Secret Key** listed in the **Application
Keys** section of your application configuration. |
| `grant_type` | This should be set to `refresh_token`. |
| `refresh_token` | This should be set to the refresh token you obtained in step 3.

The request body must be of type `application/json`.

```javascript
// Replace the ellipses with the appropriate 
// values from the table above.
const request = {
	client_id: '...',
	client_secret: '...',
	grant_type: 'refresh_token',
    refresh_token: '...'
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

This response has the same structure as the one from step 3. Note that the `refresh_token` always stays the same, so you don't need to store it again.
