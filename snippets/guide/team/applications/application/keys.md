# Application Keys

This section contains the keys necessary to start interacting with the Edlink API. Each of your company's applications will have a unique set of keys. This makes it easy to generate additional key pairs for development and testing, while keeping your client data separate and secure. These keys are used primarily for the OAuth 2.0 SSO flow that Edlink provides, and can also be used to interact with other features (e.g. the Graph API) in a more programmatic way.

## Application ID

The application ID is a randomly generated UUID that represents your [Application]() in the Edlink ecosystem. This ID is public and can safely be exposed to clients.

## Secret Key

This key is used for the token exchange phase of the OAuth 2.0 process, as well as to make a handful of other system calls. It is very important that you never expose this value to the public unless your application is specifically for development purposes. If you believe your secret key has been compromised, please contact us immediately.

## Valid Redirect URIs

This text box contains a list of your application's redirect URIs. After you send users to the OAuth 2.0 [Login URL](), Edlink will authenticate them and return them to the Redirect URI specified in the [Login Request](). The Redirect URI specified in the login request *must* be an exact match to one of the URLs in the text box.

In the event Edlink is handling a launch request (e.g. via LTI or Clever), Edlink will simply choose the *first* available redirect URI. This means that the order of your URIs does matter, and modifying the order may impact live users. If you wish to test something, we recommend creating an additional [Application](). This will allow you to specify a different set of redirect URIs.

<ul class="related">
    <li>
        <a href="">Understanding Edlink's Data Model</a>
    </li>
    <li>
        <a href="">Getting Started With SSO</a>
    </li>
</ul>

# Requested Permissions

Edlink offers a variety of functionality to developers including SSO, rostering, content integration, and grade syncing. In order to protect school data, we require that application developers specify ahead of time which functionality they intend to utilize.

Because the Edlink API is two-way, we have split all permissions into two categories: Read and Modify. If your application will modify data within the school's LMS (e.g. by [Creating an Assignment]()) then you will need to select the "Modify" option. Modify permissions encapsulate Read permissions, so you do not need to select both.

## Changing Requested Permissions

You are able to change your requested permissions at a later time. This will only impact future schools who integrate with your application. In order to receive the newly requested permissions for existing integrations, the school administrator who created the integration will need to sign into Edlink and accept the new permissions. It is **not** required to destroy and recreate an integration in order to modify permissions.