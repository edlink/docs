# Permission

Edlink stores basic information on each of the available permission scopes that applications can request and administrators can grant. The permission object contains basic metadata about the scope, and likely does not need to be used by your application directly. A reason that you may wish to access this endpoint to retrieve a list of permissions which can later be used to detect when an admin has disabled access to certain functions. You may with to update your UI or show a message to your users indicating that a feature is unavailable.

Permission IDs are stable and can be relied upon or cached as necessary. We will notify you if permissions are added or removed.

## Properties

| Property | Type | Description |
|---|---|---|
| `id` | UUID | A stable UUID representing this permission. |
| `name` | String | The formatted name of this permission. |
| `description` | String | A URL to the icon for this permission. |
| `scoped` | Boolean | Whether or not this is an application-level or a user-level permission. |
| `group` | String | The group of permissions into which this permission falls. |
| `active` | Boolean | Whether or not the permission is active. Always `true`. |

## Scoped vs. Unscoped Permissions

As the Edlink API is split into two sections - the Graph API and the User Data API - permissions are also split into two sections. Unscoped permissions allows application-level access to data available to you via the Graph API. Scoped permissions refer to individual user functions made through the User Data API with a user's access token.