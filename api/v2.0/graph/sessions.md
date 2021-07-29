# Sessions

## List Sessions

### *GET* https://ed.link/api/v2/graph/sessions

Retrieve a list of all **[Sessions](../models/external/session)**.

#### Request Parameters

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/sessions', {
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
      "created_date": "2021-07-13T17:45:27.548Z",
      "updated_date": "2021-07-13T17:45:27.548Z",
      "name": "Fall 2021",
      "start_date": "2021-07-01T00:00:00.000Z",
      "end_date": "2022-01-01T00:00:00.000Z",
      "state": "active",
      "type": "semester",
      "properties": {},
      "school_id": "00000000-0000-0000-0000-000000000000",
      "district_id": "00000000-0000-0000-0000-000000000000"
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## Fetch Session

### *GET* https://ed.link/api/v2/graph/sessions/:session\_id

Retrieve information about a specific **[Session](../models/external/session)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `session_id` | `string` | The UUID of the desired **[Session](../models/external/session)**. |

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/sessions/00000000-0000-0000-0000-000000000000', {
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
    "created_date": "2021-07-13T17:45:27.548Z",
    "updated_date": "2021-07-13T17:45:27.548Z",
    "name": "Fall 2021",
    "start_date": "2021-07-01T00:00:00.000Z",
    "end_date": "2022-01-01T00:00:00.000Z",
    "state": "active",
    "type": "semester",
    "properties": {},
    "school_id": "00000000-0000-0000-0000-000000000000",
    "district_id": "00000000-0000-0000-0000-000000000000"
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```
