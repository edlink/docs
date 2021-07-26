# Requests

We log all requests made through our API for each integration. We erase requests from our database after 30 days.
Through these endpoints, you can retrieve any recently made requests and their output.

## List Requests

### *GET* https://ed.link/api/v2/graph/requests

Retrieve a list of all requests.

#### Request Parameters

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

#### Sample Request

```javascript
// List the 5 most recent requests.
axios.get('https://ed.link/api/v2/graph/requests?$last=5', {
	headers: {
		authorization: `Bearer ${integration_access_token}`
	}
});
```

### Sample Response

```json
{
  "$data": [
    {
      "id": "00000000-0000-0000-0000-000000000000",
      "date": "2021-07-26T22:29:21.121Z",
      "start_date": "2021-07-26T22:29:20.744Z",
      "end_date": "2021-07-26T22:29:21.049Z",
      "method": "GET",
      "path": "/api/v2/graph/people",
      "status": 200,
      "properties": {
        "ip": "0.0.0.0",
        "query": {},
        "api_server": "0.0.0.0",
        "user_agent": "PostmanRuntime/7.28.1"
      },
      "input": {},
      "output": {
        ...
      },
      "person_id": null,
      "integration_id": "00000000-0000-0000-0000-000000000000"
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## Fetch Request

### *GET* https://ed.link/api/v2/graph/request/:request\_id

Retrieve information about a specific request.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `request` | `string` | The UUID of the desired request. |

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/requests/00000000-0000-0000-0000-000000000000', {
	headers: {
		authorization: `Bearer ${integration_access_token}`
	}
});
```

#### Sample Response

```json
{
  "$data": {
    "id": "00000000-0000-0000-0000-000000000000",
    "date": "2021-07-26T22:29:21.121Z",
    "start_date": "2021-07-26T22:29:20.744Z",
    "end_date": "2021-07-26T22:29:21.049Z",
    "method": "GET",
    "path": "/api/v2/graph/people",
    "status": 200,
    "properties": {
      "ip": "0.0.0.0",
      "query": {},
      "api_server": "0.0.0.0",
      "user_agent": "PostmanRuntime/7.28.1"
    },
    "input": {},
    "output": {
      ...
    },
    "person_id": null,
    "integration_id": "00000000-0000-0000-0000-000000000000"
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```
