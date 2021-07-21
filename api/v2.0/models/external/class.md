# Class
A **Class** is an instance of a **[Course](course)**.
Many **[People](person)** can be **[Enrolled](enrollment)** in a **Class**.

> In previous versions of the Edlink API, this concept was called a **[Course](course)**.
> 
> In v2.0, we've corrected some of our terminology to be more accurate and universal.
> Please review **[Migration from v1.0](../../migration)** for more information.

## Properties
| Property | Type | Description |
| -------- | ---- | ----------- |
| `id` | `string` | The UUID for the object. |
| `created_date` | `Date` | When the object was first seen by Edlink. |
| `updated_date` | `Date` | When the object was last changed in Edlink. |
| `name` | `string` | The name of the object. |
| `description` | `string` | The description of the object. |
| `picture_url` | `string` | The URL for the class's profile picture. |
| `subjects` | **[`Subject[]`](enums/subject)** | The subjects this class is associated with. |
| `grade_levels` | **[`GradeLevel[]`](enums/grade-level)** | The grade levels this class is associated with. |
| `periods` | `string[]` | The periods this class is taught. |
| `state` | **[`ClassState`](enums/class-state)** | The state of the class. |
| `locale` | `string` | The locale of the object. |
| `time_zone` | `string` | The [tz database](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) name of the object. |
| `properties` | `object` | Non-standard properties that may be of interest to the developer. |
| `session_ids` | `string[]` | The UUIDs of the associated **[Sessions](session)**. |
| `course_id` | `string` | The UUID of the associated **[Course](course)**. |
| `school_id` | `string` | The UUID of the associated **[School](school)**. |

## JSON Example
```json
{
  "id": "00000000-0000-0000-0000-000000000000",
  "created_date": "2021-07-13T17:45:27.685Z",
  "updated_date": "2021-07-13T17:45:27.685Z",
  "name": "Defense Against the Dark Arts",
  "description": null,
  "picture_url": null,
  "grade_levels": [
    "06"
  ],
  "subjects": [
    "CEDS.08"
  ],
  "periods": [
    "1"
  ],
  "state": "active",
  "locale": null,
  "time_zone": null,
  "properties": {},
  "session_ids": [
    "00000000-0000-0000-0000-000000000000"
  ],
  "course_id": "00000000-0000-0000-0000-000000000000",
  "school_id": "00000000-0000-0000-0000-000000000000"
}
```
