# Events

The Events API allows you to sync only data that has changed (deltas). Events are automatically generated when people, enrollments, terms, and organizations are created, updated, or deleted. Events are scoped to a single integration.

> Check out our full guide on the [Events API](../../../guides/v2.0/events) for in-depth instructions and examples.

## List Events

### *GET* https://ed.link/api/v2/graph/events

Retrieve a list of all available **[Events](../models/internal/event)**.

Events go back in time up to 30 days, in accordance with our data retention policy. Events should always be processed in the order in which they are returned. When paging through events, it is always recommended to page forward using `$first` and `$after`. 

While backward paging is supported, there is really no good reason to do so, and it may result in corrupted data (due to events being applied in reverse order).

#### Request Parameters

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

#### Sample Request

```javascript
// List the 5 most recent events.
axios.get('https://ed.link/api/v2/graph/events?$last=5', {
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
      "date": "2021-07-26T06:15:47.179Z",
      "type": "deleted",
      "target": "person",
      "target_id": "00000000-0000-0000-0000-000000000000",
      "integration_id": "00000000-0000-0000-0000-000000000000",
      "materialization_id": "00000000-0000-0000-0000-000000000000",
      "data": {
        ...
      }
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## Fetch Event

### *GET* https://ed.link/api/v2/graph/events/:event\_id

Retrieve information about a specific **[Event](../models/internal/event)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `event_id` | `string` | The UUID of the desired **[Event](../models/internal/event)**. |

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/events/00000000-0000-0000-0000-000000000000', {
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
    "date": "2021-07-26T06:15:47.179Z",
    "type": "deleted",
    "target": "person",
    "target_id": "00000000-0000-0000-0000-000000000000",
    "integration_id": "00000000-0000-0000-0000-000000000000",
    "materialization_id": "00000000-0000-0000-0000-000000000000",
    "data": {
      ...
    }
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```
