# Assignment
An **Assignment** can accept a **[Submission](submission)**.

> This page is under construction.

## Properties
| Property                | Type                                          | Description                                                                                        |
|-------------------------|-----------------------------------------------|----------------------------------------------------------------------------------------------------|
| `id`                    | `string`                                      | The UUID for the object.                                                                           |
| `created_date`          | `Date`                                        | When the object was first seen by Edlink.                                                          |
| `updated_date`          | `Date`                                        | When the object was last changed in Edlink.                                                        |
| `title`                 | `string`                                      | The name of the object.                                                                            |
| `description`           | `string`                                      | The description of the object. This will be used for LMS systems that support special formatting.  |
| `description_plaintext` | `string`                                      | The description of the object with special formatting removed.                                     |
| `state`                 | **[`AssignmentState`](enums/content-state)**  | The state of the assignment.                                                                       |
| `tag_ids`               | `string[]`                                    | The UUIDs of the associated **[Tags](standard)**.                                                       |
| `assignee_mode`         | **[`AssigneeMode`](enums/assignee-mode)**     | The method by which the assignment's assignees are determined.                                     |
| `assignee_ids`          | `string[]`                                    | If `assignee_mode` is set to `individuals`, this should be a list of **[Person](person)** `id`s.   |
| `due_date`              | `Date`                                        | The time at which new submissions are late for the assignment.                                     |
| `display_date`          | `Date`                                        | The time at which the assignment becomes visible.                                                  |
| `start_date`            | `Date`                                        | The time at which submissions begin to be accepted for the assignment.                             |
| `end_date`              | `Date`                                        | The time at which submissions are no longer accepted for the assignment.                           |
| `points_possible`       | `number`                                      | The number of points possible for the assignment. Only present if `grading_type` is `points`.      |
| `grading_type`          | **[`GradingType`](enums/grading-type)**       | The grading type for the assignment.                                                               |
| `submission_types`      | **[`SubmissionType`](enums/submission-type)** | The types of submissions accepted by the assignment.                                               |
| `max_attempts`          | `number`                                      | The maximum number of attempts that a **[`Submission`](submission)** for this assignment can have. |

