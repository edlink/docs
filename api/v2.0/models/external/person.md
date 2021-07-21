# Person
A **Person** within a data source.

## Properties

| Property | Type | Description |
| -------- | ---- | ----------- |
| `id` | `string` | The UUID for the object. |
| `created_date` | `Date` | When the object was first seen by Edlink. |
| `updated_date` | `Date` | When the object was last changed in Edlink. |
| `first_name` | `string` | The person's first name. |
| `middle_name` | `string` | The person's middle name. |
| `last_name` | `string` | The person's last name. | 
| `display_name` | `string` | The person's display name. |
| `picture_url` | `string` | The URL for the person's profile picture. |
| `roles` | **[`Role[]`](enums/role)** | The person's roles. |
| `email` | `string` | The person's email address. |
| `phone` | `string` | The person's phone number. |
| `locale` | `string` | The locale of the object. |
| `time_zone` | `string` | The [tz database](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) name of the object. |
| `graduation_year` | `number` | The person's expected graduation year. |
| `grade_levels` | **[`GradeLevel[]`](enums/grade-level)** | The grade levels this school is associated with. |
| `demographics` | **[`Demographics`](demographics)** | The person's demographics. |
| `properties` | `object` | Non-standard properties that may be of interest to the developer. |
| `district_id` | `string` | The UUID of the associated **[District](district)**. |
| `school_ids` | `string[]` | The UUIDs of the associated **[Schools](school)**. |

## JSON Example

```json
{
  "id": "00000000-0000-0000-0000-000000000000",
  "created_date": "2021-07-13T17:45:39.937Z",
  "updated_date": "2021-07-13T17:45:39.937Z",
  "first_name": "George",
  "middle_name": "Oscar",
  "last_name": "Bluth",
  "display_name": "Gob Bluth",
  "picture_url": "https://static.wikia.nocookie.net/arresteddevelopment/images/7/79/GOB_on_segway.jpg",
  "roles": [
    "student"
  ],
  "email": "gob.bluth@example.com",
  "phone": "12345556789",
  "locale": "en",
  "time_zone": "America/Los_Angeles",
  "graduation_year": 1996,
  "grade_levels": [ "PS" ],
  "demographics": {},
  "properties": {},
  "district_id": "00000000-0000-0000-0000-000000000000",
  "school_ids": [ "00000000-0000-0000-0000-000000000000" ]
}
```
