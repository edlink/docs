# Section
A **Section** is

## Properties
| Property | Type | Description |
| -------- | ---- | ----------- |
| `id` | `string` | The UUID for the object. |
| `created_date` | `Date` | When the object was first seen by Edlink. |
| `updated_date` | `Date` | When the object was last changed in Edlink. |
| `name` | `string` | The name of the object. |
| `description` | `string` | The description of the object. |
| `picture_url` | `string` | The URL for the class's profile picture. |
| `state` | **[`ClassState`](enums/class-state)** | The state of the class. |
| `locale` | `string` | The locale of the object. |
| `time_zone` | `string` | The [tz database](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) name of the object. |
| `properties` | `object` | Non-standard properties that may be of interest to the developer. |
| `session_ids` | `string[]` | The UUIDs of the associated **[Sessions](session)**. |

## JSON Example
```json
{
  "id": "00000000-0000-0000-0000-000000000000",
  "created_date": "2021-07-13T17:45:27.645Z",
  "updated_date": "2021-07-13T17:45:27.645Z",
  "name": "Section 3",
  "description": null,
  "picture_url": null,
  "state": "active",
  "locale": "en",
  "time_zone": "America/Chicago",
  "properties": {}
}
```
