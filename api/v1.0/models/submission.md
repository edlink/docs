# Submission

Submissions are student responses to resources (e.g. assignments or quizzes). Not all school data sources support the creation of resources. For example, Clever and Classlink provide student roster data and do not provide functionality for learning resources.

## Properties

These submission properties are available in all systems that support content integration, unless otherwise noted. Some source systems may not support all values (e.g. some systems may not allow file upload submissions). Occasionally, we will also provide special properties unique to only one system, if the functionality achieved is important enough to create a special case.

| Property | Type | Description |
|---|---|---|
| `id` | String | A string (not a UUID) that corresponds to this submission. These IDs are the LMS ID and are **not** guaranteed to be unique (even within the same source system). |
| `body` | String | The text or HTML body of the submission. |
| `url` | String | A direct link to the submission within the LMS. |
| `score` | Number | The score of the most recent attempt. |
| `created_date` | Date | The timestamp the submission was created. |
| `graded_date` | Date | The timestamp the submission was graded. |
| `late` | Boolean | Whether or not the submission is marked as `late` within the LMS. |
| `missing` | Boolean | Whether or not the submission is marked as `missing` within the LMS. |
| `attempts` | Number | The number of times that the student submitted work for this assignment. |
| `type` | String | The type of the submission. |
| `assignment` | Assignment | The assignment to which this item is submitted. |
| `source` | Source | The data source for this assignment. |