Edlink can handle and process LTI launches for single sign on.
The resulting authenticated user will be forwarded along to your application via the OAuth 2.0 redirect URI that you specify on your application settings page.
In the event that you enable more than one redirect URI, the first one listed will be used by default.

<!-- ## Generating LTI Launch Links -->

## What is Forwarded to Your Application

You do not need to implement anything beyond the standard Edlink SSO in order to receive LTI launch requests. From your application's perspective, they are
the same as any other incoming authentication request.

Edlink will receive the incoming LTI launch request from the learning management system, process the
request, and generate an authorization code in accordance with the first leg of the standard OAuth 2.0 flow. We will then redirect the user to your specified
redirect URI with the `code` query parameter set. Your application can then handle the remainder of the authentication process as described in our [Authentication](/docs/user/authentication) document.


``` javascript
https://<YOUR_REDIRECT_URI>?code=<AUTHORIZATION_CODE>
```