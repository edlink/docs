# Event

An **Event** is logged by Edlink when data is created, updated, or deleted for a **[Source](source)**.

## Properties

| Property | Type | Description |
| -------- | ---- | ----------- |
| `id` | `string` | The UUID for the object. |
| `date` | `Date` | When the event occurred. |
| `type` | **[`EventType`](enums/event-type)** | The type of the event. |
| `target` | **[`EventTarget`](enums/event-target)** | The target of the event. |
| `target_id` | `string` | The UUID of the associated object. The type of this object depends on the value of `target`. |
| `integration_id` | `string` | The UUID of the associated **[Integration](integration)**. |
| `materialization_id` | `string` | The UUID of the associated **[Materialization](materialization)**. |
| `data` | `object` | The new value of the target object after the event occurred. |

## JSON Example

```json
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
```
