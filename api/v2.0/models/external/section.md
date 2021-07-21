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
| `state` | **[`SectionState`](enums/section-state)** | The state of the section. |
| `locale` | `string` | The locale of the object. |
| `time_zone` | `string` | The [tz database](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) name of the object. |
| `periods` | `string[]` | The periods this section is taught. |
| `properties` | `object` | Non-standard properties that may be of interest to the developer. |
| `class_id` | `string` | The UUID of the associated **[Class](class)**. |

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
  "properties": {},
  "periods": [ "06" ],
  "class_id": "00000000-0000-0000-0000-000000000000"
}
```
