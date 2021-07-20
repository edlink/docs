# District
An Edlink **District** is the highest level object in
a source. There will always be exactly one **District**
for a source.

## Properties
| Property | Type | Description |
| -------- | ---- | ----------- |
| `id` | `string` | The UUID for the object. |
| `created_date` | `Date` | When the object was first seen by Edlink. |
| `updated_date` | `Date` | When the object was last changed in Edlink. |
| `name` | `string` | The name of the object. |
| `locale` | `string` | The locale of the object. |
| `time_zone` | `string` | The [tz database](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) name of the object. |
| `location` | [`Address`](address.md) | The address location of the object.
| `properties` | `object` | Non-standard properties that may be of interest to the developer. |

## JSON Example
```json
{
  "id": "00000000-0000-0000-0000-000000000000",
  "created_date": "2021-07-05T20:32:40.454Z",
  "updated_date": "2021-07-12T21:44:23.126Z",
  "name": "Gravity Falls School District",
  "locale": "en",
  "time_zone": "America/Los_Angeles",
  "location": {},
  "properties": {}
}
```
