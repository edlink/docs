Integrations are connections between a school data source (e.g. Canvas) and one of your applications. Integrations may be scoped to either the entire data source, or particular schools / courses within the data source. We encourage administrators and developers to reduce the scope of data sharing to only essential people and organizational units to reduce data transfer requirements and security risks. In addition to scoping the available data that developers can access, administrators can also limit the access and functionality of particular applications. When setting up your application, you are able to define your requested permissions. Administrators can choose to grant or deny this privileges when they are establishing an integration.

### Integration Access Tokens

Upon establishing an integration, a new access token is generated for the developer. This access token will be used to access Graph API data for the particular integration. The token is automatically scoped to the correct set of people, organizations, and permissions, so you do not have to worry about accessing data that is unauthorized.

### The Integration Object

| Property | Type | Description |
|---|---|---|
| `id` | UUID | A stable UUID representing this integration. |
| `created_date` | Date | The date upon which this integration was initially created. |
| `updated_date` | Date | The latest time upon which this integration was updated. |
| `permissions` | Array | An array of UUIDs representing the permissions that this integration has access to. |
| `scope` | String | Can be either `all` or `selected`. Whether the integration has access to all data from this source, or it is limited to certain schools / courses. |
| `targets` | Array | Optional. If `scope` is `selected`, this contains an array of UUIDs to which the integration has access. |
| `status` | String | The status of this integration. Either `inactive`, `active`, or `disabled`. |
| `access_token` | String | The access token that you can use to access Graph API data for this integration. |
| `application` | Application | Optional. Provided only for Clever and Classlink connections. |
| `source` | Source | Metadata about the source to which this integration connects. |
| `team` | Team | Metadata about the school to whom this source belongs. |
| `provider` | Provider | Metadata about the source data system (e.g. Canvas). |
| `entity` | Entity | The real-world school or district to whom this source belongs. |

#### Additional Notes

* The `access_token` will not change if permissions or targets are changed. However, it will change if an integration is destroyed and then recreated.
* The `source` cannot currently be changed after it is set. In order to provide a develop access to a new source, administrators must create a new integration.
* The `application` parameter can be safely ignored. It is used primarily for internal purposes.
* Integrations will have a status of `inactive` if they are scheduled to start automatically at a later date.
* Requests to retrieve Graph data will be denied if integrations are set to `inactive` or `disabled`.

## List Available Integrations
### *GET* https://ed.link/api/v1/integrations

Retrieve a list of integrations between your application and a school data source. There are no special parameters available for this endpoint. You must provide your application secret key in order to access this endpoint. This query allows for [standard paging parameters](/docs/graph/paginated-requests).

#### Sample Request

```javascript
const integrations = await axios.get('https://ed.link/api/v1/integrations', {
    headers: {
        authorization: `Bearer ${application_secret_key}`
    }
});
```

#### Sample Response

```json
{
    "$data": [
        {
            "id": "77a69705-41a7-49cb-0fe8-ffd425f9716f",
            "status": "active",
            "scope": "all",
            "created_date": "2020-02-14T19:26:00.188Z",
            "updated_date": "2020-02-14T19:26:00.188Z",
            "permissions": [
                "39a69700-0fe8-43a7-afa7-bd4ecc936412"
            ],
            "targets": [],
            "access_token": "HZ4MR8NyjdPiP9g8l6gKXT5Kjk9FlJa7",
            "source": {
                "id": "5d149266-95d2-42cf-8660-8b528b3bfba3",
                "status": "active",
                "name": "Edlink University Canvas",
                "created_date": "2020-02-14T17:20:06.254Z",
                "updated_date": "2020-02-14T17:20:06.254Z",
                "import_interval": 3600,
                "log_retention_time": 604800
            },
            "provider": {
                "id": "035d6dd6-1569-47b2-8ed8-63435be58078",
                "name": "Canvas",
                "application": "canvas",
                "allows_data_sync": true
            },
            "team": {
                "id": "d078e26d-9fcc-4f2b-b19f-430891906061",
                "type": "district",
                "name": "Edlink University",
                "alias": "edu",
                "street_address": "1011 San Jacinto Blvd",
                "unit_number": "Ste 303",
                "city": "Austin",
                "state": "TX",
                "zip": "78701",
                "country": "United States"
            },
            "entity": null
        },
        { ... }
    ]
}
```

## Fetch A Single Integration
### *GET* https://ed.link/api/v1/integrations/:id

Retrieve information about a single integration. There are no special parameters available for this endpoint. You must provide your application secret key in order to access this endpoint.

#### Sample Request

```javascript
const integrations = await axios.get('https://ed.link/api/v1/integrations/77a69705-41a7-49cb-0fe8-ffd425f9716f', {
    headers: {
        authorization: `Bearer ${application_secret_key}`
    }
});
```

#### Sample Response

```json
{
    "$data": {
        "id": "77a69705-41a7-49cb-0fe8-ffd425f9716f",
        "status": "active",
        "scope": "all",
        "created_date": "2020-02-14T19:26:00.188Z",
        "updated_date": "2020-02-14T19:26:00.188Z",
        "permissions": [
            "39a69700-0fe8-43a7-afa7-bd4ecc936412"
        ],
        "targets": [],
        "access_token": "HZ4MR8NyjdPiP9g8l6gKXT5Kjk9FlJa7",
        "source": {
            "id": "5d149266-95d2-42cf-8660-8b528b3bfba3",
            "status": "active",
            "name": "Edlink University Canvas",
            "created_date": "2020-02-14T17:20:06.254Z",
            "updated_date": "2020-02-14T17:20:06.254Z",
            "import_interval": 3600,
            "log_retention_time": 604800
        },
        "provider": {
            "id": "035d6dd6-1569-47b2-8ed8-63435be58078",
            "name": "Canvas",
            "application": "canvas",
            "allows_data_sync": true
        },
        "team": {
            "id": "d078e26d-9fcc-4f2b-b19f-430891906061",
            "type": "district",
            "name": "Edlink University",
            "alias": "edu",
            "street_address": "1011 San Jacinto Blvd",
            "unit_number": "Ste 303",
            "city": "Austin",
            "state": "TX",
            "zip": "78701",
            "country": "United States"
        },
        "entity": null
    }
}
```