# Materializations

Our system schedules a **Materialization** when any of the following things happen:

 * An **[Integration](../models/internal/integration)**'s sharing rules change
 * Updated data is available from a **[Source](../models/internal/source)** via our syncs

During a materialization, the data returned by the Graph API updates.

## List Materializations

### *GET* https://ed.link/api/v2/graph/materializations

Retrieve a list of all materializations.

#### Request Parameters

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

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

Retrieve information about a specific materialization.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `materialization_id` | `string` | The UUID of the desired **[Materialization](../models/external/materialization)**. |

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
