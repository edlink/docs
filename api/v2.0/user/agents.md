# Agents

> This page is under construction. User API v2 is in beta and is subject to change.

## List Agents

### *GET* https://ed.link/api/v2/my/agents

Retrieve a list of **[Agents](../models/external/agent)** that the current user is associated with. This includes all agent relationships in which the current user is the `observer` or the `target`.

#### Request Parameters

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/my/agents', {
	headers: {
		authorization: `Bearer ${person_access_token}`
	}
});
```

#### Sample Response

```json
{
  "$data": [
    {
      "id": "00000000-0000-0000-0000-000000000000",
      "relationship": "parent",
      "properties": {},
      "observer_id": "00000000-0000-0000-0000-000000000000",
      "target_id": "00000000-0000-0000-0000-000000000000"
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## Fetch Agent

### *GET* https://ed.link/api/v2/my/agents/:agent_id

Retrieve information about a specific **[Agent](../models/external/agent)** that the current user is associated with.

#### Request Parameters

| Parameter  | Type     | Description                                                    |
|------------|----------|----------------------------------------------------------------|
| `agent_id` | `string` | The UUID of the desired **[Agent](../models/external/agent)**. |

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/my/agents/00000000-0000-0000-0000-000000000000', {
	headers: {
		authorization: `Bearer ${person_access_token}`
	}
});
```

#### Sample Response

```json
{
  "$data": {
    "id": "00000000-0000-0000-0000-000000000000",
    "relationship": "parent",
    "properties": {},
    "observer_id": "00000000-0000-0000-0000-000000000000",
    "target_id": "00000000-0000-0000-0000-000000000000"
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```
