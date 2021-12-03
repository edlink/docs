# Application Settings

This page contains details about your developer application. It also allows you to set various `Permissions` for your district integrations and select the data `Sources` that school districts are allowed to connect.

## Application Keys

These keys help Edlink identify your application during the [OAuth 2.0 Authentication]() process and various system-level API calls.

Your `Application ID` is a public UUID that identifies your application to Edlink. It can be safely shared with the client and does not need to be shared securely. You may notice it pop up in various places such as your [Integration Link]().

Your `Application Secret` identifies your application to Edlink during the OAuth 2.0 [token exchange]() and when you [request details about your integrated districts](). This value must be kept **secret**. If you believe your secret key has become compromised, please contact us immediately.

<ul class="related">
    <li>
        <a href="">Keeping Your Keys Safe</a>
    </li>
    <li>
        <a href="">Listing Connected Districts</a>
    </li>
</ul>

## Allowed Providers

While Edlink supports a number of different LMS, SIS, and SSO providers, you may not want to authorize schools to connect each and every one of them.

On the `Allowed Providers` list, you can select which `Providers` you would like to enable or disable.

Unselecting a `Provider` will **not** disconnect existing integrations, but it will disallow future school districts from connecting `Sources` of that type.

<ul class="related">
    <li>
        <a href="">Selecting Source Providers</a>
    </li>
</ul>

## Application Permissions

In order to keep student data safe, Edlink requires that you specify the `Permissions` your application is planning to utilize. Only permissions selected on this list will be available to your application through the Edlink API.

You are welcome to change these permissions at any time, however, this will not affect existing `Integrations`. In order to update the permissions of an existing integration, the school administrator will have to [approve the new permissions]() via their Edlink dashboard.

<ul class="related">
    <li>
        <a href="">Selecting Application Permissions</a>
    </li>
    <li>
        <a href="">Updating Permissions</a>
    </li>
</ul>