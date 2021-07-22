# Integrations

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