# Authorization

## Authorizing Graph API Requests

Accessing the Edlink Graph API requires your secret key, which is available after you create an application in your Edlink Dashboard.
Your secret key acts as a bearer token and conveys your identity to Edlink. Therefore, all requests must be made over HTTPS to avoid exposing the key to the public.
We will redirect or reject all requests not made via HTTPS.

Your application's secret key can be used to [retrieve a list of active integrations](/docs/graph/integrations).
This list contains all of the different individual school data sources that have connected to your application.
When school administrators grant access to their data source (e.g. Canvas), a new integration will appear on the list. When they revoke access, it will be removed.
Each integration contains its own access token that you will use to actually data from the data source. This access token is sent in the same fashion as your application's token.

## Making Requests With An Access Token

To make a request to a protected endpoint - which is virtually all endpoints - you must include your secret key in an HTTP header called `Authorization`.
Edlink uses this header to identify incoming requests. Set the `Authorization` header to a value of the word `Bearer`, followed by a single space, followed by your key.

Here is a sample request that loads a list of the data sources to which you have been granted access.

``` javascript
const sources = await axios.get('https://ed.link/api/v1/graph/integrations', {
    headers: {
        'Authorization': 'Bearer XxYUqqrxHBo6yWBqcry8b73GhibnrQyq'
    }
});
```

## Authorizing User API Requests

With all requests to Edlink, we require that you provide your Edlink secret key. You can read more about the API key and how to properly attach it to your requests [on the equivalent document in the Graph API section](/docs/graph/authorization). The primary reason that we require this API key, even when making requests with a [user's bearer token](/docs/user/authentication), is to safeguard user data and ensure that a token is only being used the application to which it was issued.