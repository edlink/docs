# School

An Edlink **School** represents a school within a data source. There will always be at least one school.

If no schools are present within a data source, we will create a district office placeholder school. For
example, `Edlink University (District Office)`. In some cases, this school will be generated to store any classes that
are not associated with a school within the data source.

## Properties

| Property | Type | Description |
| -------- | ---- | ----------- |
| `id` | `string` | The UUID for the object. |
| `created_date` | `Date` | When the object was first seen by Edlink. |
| `updated_date` | `Date` | When the object was last changed in Edlink. |
| `name` | `string` | The name of the object. |
| `grade_levels` | **[`GradeLevel[]`](enums/grade-level)** | The grade levels this school is associated with. |
| `locale` | `string` | The locale of the object. |
| `time_zone` | `string` | The [tz database](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) name of the object. |
| `location` | **[`Address`](address)** | The address location of the object.
| `properties` | `object` | Non-standard properties that may be of interest to the developer. |
| `district_id` | `string` | The UUID of the associated **[District](district)**. |

## JSON Example

```json
{
  "id": "00000000-0000-0000-0000-000000000000",
  "created_date": "2021-07-05T20:32:40.454Z",
  "updated_date": "2021-07-12T21:44:23.126Z",
  "name": "Springfield Elementary School",
  "grade_levels": [
    "01",
    "02",
    "03",
    "04",
    "05"
  ],
  "locale": "en",
  "time_zone": "America/Chicago",
  "location": {},
  "properties": {},
  "district_id": "00000000-0000-0000-0000-000000000000"
}
```
