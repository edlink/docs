Edlink stores basic information on each of the available permission scopes that applications can request and administrators can grant. The permission object contains basic metadata about the scope, and likely does not need to be used by your application directly. A reason that you may wish to access this endpoint to retrieve a list of permissions which can later be used to detect when an admin has disabled access to certain functions. You may with to update your UI or show a message to your users indicating that a feature is unavailable.

Permission IDs are stable and can be relied upon or cached as necessary. We will notify you if permissions are added or removed.

### The Permission Object
| Property | Type | Description |
|---|---|---|
| `id` | UUID | A stable UUID representing this permission. |
| `name` | String | The formatted name of this permission. |
| `description` | String | A URL to the icon for this permission. |
| `scoped` | Boolean | Whether or not this is an application-level or a user-level permission. |
| `group` | String | The group of permissions into which this permission falls. |
| `active` | Boolean | Whether or not the permission is active. Always `true`. |

### Scoped vs. Unscoped Permissions

As the Edlink API is split into two sections - the Graph API and the User Data API - permissions are also split into two sections. Unscoped permissions allows application-level access to data available to you via the Graph API. Scoped permissions refer to individual user functions made through the User Data API with a user's access token.

## List All Permissions
### *GET* https://ed.link/api/v1/permissions

Retrieve a list of all active permissions and their associated metadata. There are no special parameters available for this endpoint. This query allows for [standard paging parameters](/docs/graph/paginated-requests).

#### Sample Request

```javascript
const permissions = await axios.get('https://ed.link/api/v1/permissions');
```

#### Sample Response

```json
{
    "$data": [
        {
            "id": "8a5c2e39-aa7a-4229-99b3-6a4d46de9c0b",
            "created_date": "2019-11-18T00:18:19.088Z",
            "updated_date": "2019-11-18T00:18:19.088Z",
            "scoped": true,
            "group": "authentication",
            "name": "Single Sign On",
            "description": "Allows end users to sign in using their credentials from the selected source.",
            "active": true
        },
        { ... }
    ]
}
```

## Fetch A Single Permission
### *GET* https://ed.link/api/v1/permissions

Retrieve information about a single permission. No additional data will be provided by this endpoint that is not also provided in the endpoint above. It is simply offered for convenience.

#### Sample Request

```javascript
const permissions = await axios.get('https://ed.link/api/v1/permissions/8a5c2e39-aa7a-4229-99b3-6a4d46de9c0b');
```

#### Sample Response

```json
{
    "$data": {
        "id": "8a5c2e39-aa7a-4229-99b3-6a4d46de9c0b",
        "created_date": "2019-11-18T00:18:19.088Z",
        "updated_date": "2019-11-18T00:18:19.088Z",
        "scoped": true,
        "group": "authentication",
        "name": "Single Sign On",
        "description": "Allows end users to sign in using their credentials from the selected source.",
        "active": true
    }
}
```