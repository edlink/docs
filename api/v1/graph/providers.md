Edlink stores basic information on each of the data providers to which it connects connects. These data providers may be learning management systems (LMSs), student information systems (SISs), or even other data connectors such as Classlink and Clever. The provider object contains basic metadata about each system, and likely does not need to be used by your application. A reason that you may wish to access this endpoint is to automatically construct a list of the systems to which your product connects.

### The Provider Object

| Property | Type | Description |
|---|---|---|
| `id` | UUID | A stable UUID representing this provider. |
| `application` | String | The internal name of this provider. |
| `name` | String | The formatted name of this provider. |
| `icon_url` | String | A URL to the icon for this provider. |
| `configuration` | JSON | The required configuration parameters to set up a new connection to this provider. |
| `requires_administrator_login` | Boolean | Whether this provider requires an administrator account to activate. |
| `requires_administrator_consent` | Boolean | Whether this provider requires an administrator consent step to activate. |
| `allows_data_sync` | Boolean | Whether this provider allows full roster data syncing. |
| `requires_remote_configuration` | Boolean | Whether this provider can be set up through Edlink or must be configured through an outside platform. |

## List All Providers
### *GET* https://ed.link/api/v1/providers

Retrieve a list of all active providers and their associated metadata. There are no special parameters available for this endpoint. This query allows for [standard paging parameters](/docs/graph/paginated-requests).

#### Sample Request

```javascript
const providers = await axios.get('https://ed.link/api/v1/providers');
```

#### Sample Response

```json
{
    "$data": [
        {
            "id": "035d6dd6-1569-47b2-8ed8-63435be58078",
            "created_date": "2019-11-18T00:19:30.432Z",
            "updated_date": "2019-11-18T00:19:30.432Z",
            "application": "canvas",
            "name": "Canvas",
            "icon_url": "https://ed.link/source/canvas.png",
            "configuration": {
                "url": { ... },
                "application_id": { ... },
                "application_secret": { ... }
            },
            "requires_administrator_login": true,
            "requires_administrator_consent": false,
            "allows_data_sync": true,
            "requires_remote_configuration": false
        },
        { ... }
    ]
}
```

## Fetch A Single Provider
### *GET* https://ed.link/api/v1/providers/:id

Retrieve information about a single provider. No additional data will be provided by this endpoint that is not also provided in the endpoint above. It is simply offered for convenience.

#### Sample Request

```javascript
const provider = await axios.get('https://ed.link/api/v1/providers/035d6dd6-1569-47b2-8ed8-63435be58078');
```

#### Sample Response

```json
{
    "$data": {
        "id": "035d6dd6-1569-47b2-8ed8-63435be58078",
        "created_date": "2019-11-18T00:19:30.432Z",
        "updated_date": "2019-11-18T00:19:30.432Z",
        "application": "canvas",
        "name": "Canvas",
        "icon_url": "https://ed.link/source/canvas.png",
        "configuration": {
            "url": { ... },
            "application_id": { ... },
            "application_secret": { ... }
        },
        "requires_administrator_login": true,
        "requires_administrator_consent": false,
        "allows_data_sync": true,
        "requires_remote_configuration": false
    }
}
```