# Submission Flag
A **Submission Flag** describes additional information about the state of a
**[Submission](../submission)**. A submission may have all, some, or none of these flags.

The values of this enum are of type `string`.

## Values
| Value     | Description                                                               |
|-----------|---------------------------------------------------------------------------|
| `missing` | The assignee has not submitted their work, and the `due_date` has passed. |
| `late`    | The assignee submitted their work after the `due_date` had passed.        |
| `excused` | The assignee is excused from making a submission for this assignment.     |
