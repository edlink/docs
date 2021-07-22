# Assignment
An **Assignment** can accept a **[Submission](submission)**.

## Properties
| Property | Type | Description |
| -------- | ---- | ----------- |
| `id` | `string` | The UUID for the object. |
| `created_date` | `Date` | When the object was first seen by Edlink. |
| `updated_date` | `Date` | When the object was last changed in Edlink. |
| `title` | `string` | The name of the object. |
| `description` | `string` | The description of the object. |
| `description_plaintext` | `string` | The description of the object with special formatting removed. |
| `state` | **[`ContentState`](enums/content-state)** | The state of the assignment. |
| `tag_ids` | `string[]` | The UUIDs of the associated **[Tags](tag)**. |
| `updated_date` | `Date` | When the object was last changed in Edlink. |
| `assignee_type` | **[`AssigneeType`](enums/assignee-type)** | The type of assignees. |
| `assignee_ids` | `Person[]` or `Section[]` or `Class[]` | The UUIDs of the associated **[People](person)**, **[Sections](section)**, or **[Classes](class)**, depending on the value of `assignee_type`.
| `due_date` | `Date` | The time at which new submissions are late for the assignment. |
| `display_date` | `Date` | The time at which the assignment becomes visible. |
| `start_date` | `Date` | The time at which submissions begin to be accepted for the assignment. |
| `end_date` | `Date` | The time at which submissions are no longer accepted for the assignment. |
| `points_possible` | `number` | The number of points possible for the assignment. Only present if `grading_type` is `points`.
| `grading_type` | **[`GradingType`](enums/grading-type)** | The grading type for the assignment. |
| `submission_types` | **[`SubmissionType`](enums/submission-type)** | The types of submissions accepted by the assignment. |
| `max_attempts` | `number` | The maximum number of **[`SubmissionAttempt`](submission-attempt)** that a **[`Submission`](submission)** for this assignment can have. |

## JSON Example
```json
{}
```
