# Materializations

## List Materializations

### *GET* https://ed.link/api/v2/graph/materializations

Retrieve a list of all **[Materializations](../models/internal/materialization)**.

#### Request Parameters

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
// List the 5 most recent materializations.
axios.get('https://ed.link/api/v2/graph/materializations?$last=5', {
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
      "created_date": "2021-07-13T20:00:54.521Z",
      "updated_date": "2021-07-13T21:02:22.330Z",
      "state": "complete",
      "priority": 0,
      "source_id": "00000000-0000-0000-0000-000000000000",
      "integration_id": "00000000-0000-0000-0000-000000000000"
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## Fetch Materialization

### *GET* https://ed.link/api/v2/graph/materialization/:materialization\_id

Retrieve information about a specific **[Materialization](../models/internal/materialization)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `materialization_id` | `string` | The UUID of the desired **[Materialization](../models/internal/materialization)**. |

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/materializations/00000000-0000-0000-0000-000000000000', {
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
    "created_date": "2021-07-13T20:00:54.521Z",
    "updated_date": "2021-07-13T21:02:22.330Z",
    "state": "complete",
    "priority": 0,
    "source_id": "00000000-0000-0000-0000-000000000000",
    "integration_id": "00000000-0000-0000-0000-000000000000"
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```
