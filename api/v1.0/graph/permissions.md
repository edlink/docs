# Permissions

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
### *GET* https://ed.link/api/v1/permissions/:permission_id

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