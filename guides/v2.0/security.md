# Security

When using the Edlink API, it's important to keep security in mind. As student data is sensitive, making sure it doesn't fall into the wrong hands is crucial.

## Keeping Secrets

One of the most important facets of keeping a secure connection with Edlink is ensuring that your secrets stay in your control.

There are many secrets that need to be kept private, and the consequences for losing any of them could be problematic, to say the least.

Among the most important of these is a user's `access_token` and `refresh_token`. During the [user authorization flow](authorization), these tokens allow you to act on behalf of a user in the Edlink API. 

Another important secret is your application's **Secret Key**. This key can be found on your application's configuration page, and it allows us to verify your identity during the [user authorization flow](authorization).

Finally, there's your **Integration Access Tokens**. These are the tokens you use to make Graph API requests, and are found on your integration summary page.

To ensure best security practices, we encourage the following:
 
 1. **Never pass these keys to the client-side of your application.** This means, in short, that you should only ever handle secrets in the backend (server-side), and you should never send secrets to any code that runs on an end-user's computer. **This is a MUST.**
 2. **Never hard-code a secret.** Your code repository should never hold a secret key. We recommend using tools like [Keybase](https://keybase.io/) that are end-to-end encrypted, or physical media like USB flash drives that never leave your sight to transfer secrets.
 3. **Want to go the extra mile?** We recommend using a secret manager like [Google Secret Manager](https://cloud.google.com/secret-manager) to store your application's **Secret Key**. Using tools like these, you can ensure only authorized users and machines will have access. You can configure your application to programmatically retrieve the secret as necessary. You can quickly grant or revoke access when employees join or leave your organization.

## Don't Rely On Email Addresses

**[Click here to read our blog post about why email addresses aren't a good way to match users.](https://ed.link/community/why-you-shouldnt-match-users-by-email-address/)**

In short, we recommend the following:
 1. **DON'T use email addresses to identify a user.** Most LMS and SIS systems do not verify email addresses for an account. This means you can't trust that whoever is logging in really owns the email address associated with their **[Person](../../api/v2.0/models/external/person)**.
 2. **DO use `id`s to identify a user.** Even if a **[Person](../../api/v2.0/models/external/person)**'s email address changes, their Edlink `id` won't change. The Edlink `id` is tied to their account within the source data provider.

## Keep Your Data Close

You should always be mindful of the data you're sending to the client. Make sure you're not exposing roster data, assignments, or grades to users who shouldn't have access to them.

## Checking State During Auth

If you aren't doing it already, it's considered a good security practice to set the `state` parameter during the OAuth 2.0 flow. Doing so can protect against [cross-site request forgery attacks](https://en.wikipedia.org/wiki/Cross-site_request_forgery). 

We cover this in our guide on the [user authorization flow](authorization).
