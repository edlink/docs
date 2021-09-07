# Materialization

Our system schedules a **Materialization** when any of the following things happen:

* An **[Integration](integration)**'s sharing rules change
* Updated data is available for a **[Source](source)** via our syncs

During a materialization, the data returned by the Graph API updates.

## Properties

| Property | Type | Description |
| -------- | ---- | ----------- |
| `id` | `string` | The UUID for the object.<br/>**[$filter operators](../../../../guides/v2.0/filtering-results):** `equals` `in` `not in` |
| `created_date` | `Date` | When the object was first created by Edlink. |
| `updated_date` | `Date` | When the object was last changed in Edlink. Typically, this is the time of completion. |
| `state` | **[`MaterializationState`](enums/materialization-state)** | The state of the materialization. |
| `priority` | `number` | The priority of the materialization. |
| `integration_id` | `string` | The UUID of the associated **[Integration](integration)**. |
| `source_id` | `string` | The UUID of the associated **[Source](source)**. |

## JSON Example

```json
{
  "id": "00000000-0000-0000-0000-000000000000",
  "created_date": "2021-07-13T20:00:54.521Z",
  "updated_date": "2021-07-13T21:02:22.330Z",
  "state": "complete",
  "priority": 0,
  "source_id": "00000000-0000-0000-0000-000000000000",
  "integration_id": "00000000-0000-0000-0000-000000000000"
}
```
