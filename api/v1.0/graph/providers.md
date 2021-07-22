# Providers

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