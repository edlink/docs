Edlink can handle and process Clever Instant Login requests for single sign on.
The resulting authenticated user will be forwarded along to your application via the OAuth 2.0 redirect URI that you specify on your application settings page.
In the event that you enable more than one redirect URI, the first one listed will be used by default.

## What is Forwarded to Your Application

You do not need to implement anything beyond the standard Edlink SSO in order to receive Clever Login requests. From your application's perspective, they are
the same as any other incoming authentication request.

Edlink will receive the incoming Clever Login request, process the
request, and generate an authorization code in accordance with the first leg of the standard OAuth 2.0 flow. We will then redirect the user to your specified
redirect URI with the `code` query parameter set. Your application can then handle the remainder of the authentication process as described in our [Authentication](/docs/guides/v1.0/authentication) document.


```
https://<YOUR_REDIRECT_URI>?code=<AUTHORIZATION_CODE>
```

## Handling Clever Library Users

Clever Library presents a unique opportunity for developers to grow their audience and client base. However, it comes at the cost of building out support for users who are part of an unknown school district. Edlink can handle authentication for these semi-anonymous teachers and students, but it is currently an opt-in feature. If this is something that you are looking for, please [contact us](/support) and we can discuss how to set it up and any possible implications from a technical perspective.
