# Agents

## List Agents

### *GET* https://ed.link/api/v2/graph/agents

Retrieve a list of all **[Agents](../models/external/agent)**.

#### Request Parameters

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/agents', {
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

### *GET* https://ed.link/api/v2/graph/agent/:agent\_id

Retrieve information about a specific **[Agent](../models/external/agent)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `session_id` | `string` | The UUID of the desired **[Agent](../models/external/agent)**. |

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/agents/00000000-0000-0000-0000-000000000000', {
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
    "relationship": "parent",
    "properties": {},
    "observer_id": "00000000-0000-0000-0000-000000000000",
    "target_id": "00000000-0000-0000-0000-000000000000"
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```
