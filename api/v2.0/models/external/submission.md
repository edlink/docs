# Submission
A **Submission** describes a **[Person](person)**'s work 
associated with an **[Assignment](assignment)**.

## Properties
| Property            | Type                                            | Description                                                                                                      |
|---------------------|-------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| `id`                | `string`                                        | The UUID for the object.                                                                                         |
| `created_date`      | `Date`                                          | When the object was created in the source.                                                                       |
| `updated_date`      | `Date`                                          | When the object was last updated in the source.                                                                  |
| `state`             | **[`SubmissionState`](enums/submission-state)** | The state of the submission.                                                                                     |
| `flags`             | **[`SubmissionFlag[]`](enums/submission-flag)** | The flags for the submission. All, some, or none of the possible flags may be included.                          |
| `attempts`          | **[`Attempt[]`](attempt)**                      | All of the attempts the assignee has made for this submission.                                                   |
| `grade_comment`     | `string`                                        | An optional comment left by the grader.                                                                          |
| `grade_points`      | `number`                                        | The numerical representation of the grade, if applicable. (i.e. `96`)                                            |
| `grade`             | `string`                                        | The string representation of the grade, if applicable. (i.e. `A+`)                                               |
| `extra_attempts`    | `string`                                        | The number of extra attempts the assignee is allowed beyond the **[`Assignment`](assignment)**'s `max_attempts`. |
| `override_due_date` | `Date`                                          | The `due_date` for this particular assignee, overriding that of the **[`Assignment`](assignment)**.              |
| `grader_id`         | `string`                                        | The UUID of the **[`Person`](person)** who grades the submission.                                                |
| `person_id`         | `string`                                        | The UUID of the **[`Person`](person)** who is the assignee of the submission.                                    |
