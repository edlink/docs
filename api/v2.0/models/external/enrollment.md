# Enrollment
An **Enrollment** describes a **[Person](person)**'s relationship with a **[Class](class)**.

Optionally, in systems that support **[Sections](section)**, an **Enrollment** can also refer to a specific **[Section](section)** associated with the **[Class](class)**.

## Properties
| Property | Type | Description |
| -------- | ---- | ----------- |
| `id` | `string` | The UUID for the object. |
| `created_date` | `Date` | When the object was first seen by Edlink. |
| `updated_date` | `Date` | When the object was last changed in Edlink. |
| `start_date` | `Date` | When the enrollment period is scheduled to start. |
| `end_date` | `Date` | When the enrollment period is scheduled to end. |
| `role` | **[`Role`](enums/role)** | The **[Person](person)**'s role in this class. Note that this can differ from their `Person.roles`. For instance, a teacher could be listed as a student in a professional development course. |
| `primary` | `boolean` | If there are multiple teachers, this will indicate the primary teacher, if there is one. |
| `state` | **[`EnrollmentState`](enums/enrollment-state)** | The state of the enrollment. |
| `properties` | `object` | Non-standard properties that may be of interest to the developer. |
| `person_id` | `string` | The UUID of the associated **[Person](person)**. |
| `class_id` | `string` | The UUID of the associated **[Class](class)**. |
| `section_id` | `string` | The UUID of the associated **[Section](section)**. |

## JSON Example
```json
{
    "id": "00000000-0000-0000-0000-000000000000",
    "created_date": "2021-07-13T17:45:27.674Z",
    "updated_date": "2021-07-13T17:45:27.674Z",
    "start_date": null,
    "end_date": null,
    "role": "teacher",
    "primary": null,
    "state": "active",
    "properties": {},
    "person_id": "00000000-0000-0000-0000-000000000000",
    "class_id": "00000000-0000-0000-0000-000000000000",
    "section_id": "00000000-0000-0000-0000-000000000000"
}
```
