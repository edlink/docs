# Assignment

An assignment is a piece of course work inside of the LMS. Typically assignments will have a due date and point value. Students may or may not submit work in response to a particular assignment.

Assignments have a variety of properties that can be used to achieve the learning experience that you're looking for within the LMS. These properties are available in all systems that support content integration, unless otherwise noted. Some source systems may not support all values (e.g. some systems may not allow file upload submissions to an assignment). Occasionally, we will also provide special properties unique to only one system, if the functionality achieved is important enough to create a special case.

## Properties

| Property | Type | Description |
|---|---|---|
| `id` | String | A string (not a UUID) that corresponds to this assignment. These IDs are the LMS ID and are **not** guaranteed to be unique (even within the same source system). |
| `description` | String | The assignment description or instructions in full HTML. |
| `description_plaintext` | String | The assignment description or instructions in plaintext for systems that do not support HTML bodies. |
| `display_date` | Date | The timestamp when the assignment will be visible to students. |
| `due_date` | Date | The timestamp when the assignment will be due for students. |
| `lock_date` | Date | The timestamp when late submissions will no longer be accepted. |
| `points_possible` | Number | The point value for the assignment. |
| `grading_type` | String | The grading scale. Typically `points`. |
| `published` | Boolean | Whether or not the assignment is published. |
| `title` | String | The assignment title. |
| `url` | String | The URL to the assignment within the LMS. |
| `submission_types` | String [] | The allowed submission types. |
| `personalized` | Boolean | Whether or not this is assigned to all students. |
| `students` | UUID [] | An array of `person_id`s of the students to whom this item is assigned (if `personalized` is `true`). |
| `course` | Organization | The course to which this item is assigned. |
| `source` | Source | The data source for this assignment. |
