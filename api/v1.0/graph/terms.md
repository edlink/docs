# Terms

## List All Terms
### *GET* https://ed.link/api/v1/graph/terms

Retrieve a list of all terms. This query allows for [standard paging parameters](/docs/graph/paginated-requests).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v1/graph/terms', {
    headers: {
        authorization: `Bearer ${integration_access_token}`
    }
});
```

#### Sample Response

```json
{
    "$data": [
        {
            "id": "3263aea2-52cf-4fc1-8a59-d4641ebfb206",
            "name": "Default Term",
            "created_date": "2019-11-19T17:13:43.661Z",
            "updated_date": "2019-11-19T17:13:43.661Z",
            "start_date": null,
            "end_date": null,
            "source": {
                "id": "13b7a412-b692-4836-9513-62e7a5894ee5"
            }
        },
        { ... }
    ]
}
```

## Fetch A Term
### *GET* https://ed.link/api/v1/graph/terms/:id

Retrieve information about a specific term. No additional data will be provided by this endpoint that is not also provided in the endpoint above. It is simply offered for convenience.

#### Sample Request

```javascript
axios.get('https://ed.link/api/v1/graph/terms/3263aea2-52cf-4fc1-8a59-d4641ebfb206', {
    headers: {
        authorization: `Bearer ${integration_access_token}`
    }
});
```

#### Sample Response

```json
{
    "$data": {
        "id": "3263aea2-52cf-4fc1-8a59-d4641ebfb206",
        "name": "Default Term",
        "created_date": "2019-11-19T17:13:43.661Z",
        "updated_date": "2019-11-19T17:13:43.661Z",
        "start_date": null,
        "end_date": null,
        "source": {
            "id": "13b7a412-b692-4836-9513-62e7a5894ee5"
        }
    }
}
```