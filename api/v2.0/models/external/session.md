# Session
A **Session** describes any sort of grading period, such as
a semester, term, or school year.

## Properties
| Property | Type | Description |
| -------- | ---- | ----------- |
| `id` | `string` | The UUID for the object.<br/>**[$filter operators](../../../../guides/v2.0/filtering-results):** `equals` `in` `not in` |
| `created_date` | `Date` | When the object was first seen by Edlink. |
| `updated_date` | `Date` | When the object was last changed in Edlink.<br/>**[$filter operators](../../../../guides/v2.0/filtering-results):** `equals` `gt` `lt` `gte` `lte` |
| `name` | `string` | The name of the object.<br/>**[$filter operators](../../../../guides/v2.0/filtering-results):** `equals` `starts with` `contains` `in` `not in` `is known` `is unknown` |
| `start_date` | `Date` | When the session is scheduled to start.<br/>**[$filter operators](../../../../guides/v2.0/filtering-results):** `equals` `gt` `lt` `gte` `lte`  |
| `end_date` | `Date` | When the session is scheduled to end.<br/>**[$filter operators](../../../../guides/v2.0/filtering-results):** `equals` `gt` `lt` `gte` `lte`  |
| `state` | **[`SessionState`](enums/session-state)** | The state of the session. |
| `type` | **[`SessionType`](enums/session-type)** | The type of the session. |
| `properties` | `object` | Non-standard properties that may be of interest to the developer. |
| `identifiers` | **[`Identifier[]`](identifier)** | Additional IDs associated with the object. |
| `school_id` | `string` | The UUID of the associated **[School](school)**. |
| `district_id` | `string` | The UUID of the associated **[District](district)**. |

## JSON Example
```json
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
```
