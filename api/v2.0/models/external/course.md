# Course
A **Course** is a plan of study. Most of the time, many **[Classes](class)** 
of a single **Course** are taught in the same **[Session](session)**.

For example, a school offers a Data Structures & Algorithms **Course**.
There might be several **[Classes](class)** of that course, each with
a different teacher and a different set of students enrolled in it.

You might imagine that a **Course** would be found in your university's
course listing, whereas a **[Class](class)** or **[Section](section)** would be what you 
actually **[Enrolled](enrollment)** in during the class registration period.

> In previous versions of the Edlink API, **Course** had a different meaning.
> That meaning has been adapted to the **[Class](class)** object.
> 
> In v2.0, we've corrected some of our terminology to be more accurate and universal.
> Please review **[Migration from v1.0](../../migration)** for more information.

## Properties
| Property | Type | Description |
| -------- | ---- | ----------- |
| `id` | `string` | The UUID for the object.<br/>**[$filter operators](../../../../guides/v2.0/filtering-results):** `equals` `in` `not in` |
| `created_date` | `Date` | When the object was first seen by Edlink. |
| `updated_date` | `Date` | When the object was last changed in Edlink.<br/>**[$filter operators](../../../../guides/v2.0/filtering-results):** `equals` `gt` `lt` `gte` `lte` |
| `name` | `string` | The name of the object. |
| `code` | `string` | The course code.<br/>**[$filter operators](../../../../guides/v2.0/filtering-results):** `equals` `in` `not in` `is known` `is unknown` |
| `grade_levels` | **[`GradeLevel[]`](enums/grade-level)** | The grade levels this course is associated with. |
| `subjects` | **[`Subject[]`](enums/subject)** | The subjects this course is associated with. |
| `properties` | `object` | Non-standard properties that may be of interest to the developer. |
| `session_id` | `string` | The UUID of the associated **[Session](session)**. |
| `school_id` | `string` | The UUID of the associated **[School](school)**.<br/>**[$filter operators](../../../../guides/v2.0/filtering-results):** `equals` `in` `not in` |
| `district_id` | `string` | The UUID of the associated **[District](district)**. |

## JSON Example
```json
{
  "id": "00000000-0000-0000-0000-000000000000",
  "created_date": "2021-07-13T17:45:27.570Z",
  "updated_date": "2021-07-13T17:45:27.570Z",
  "name": "Data Structures & Algorithms",
  "code": "CS 425",
  "grade_levels": [],
  "subjects": [
    "CEDS.21"
  ],
  "properties": {},
  "session_id": "00000000-0000-0000-0000-000000000000",
  "school_id": "00000000-0000-0000-0000-000000000000",
  "district_id": "00000000-0000-0000-0000-000000000000"
}
```
