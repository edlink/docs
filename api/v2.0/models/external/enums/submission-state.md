# Submission State
An **Submission State** describes the state of a
**[Submission](../submission)**.

The values of this enum are of type `string`.

> This page is under construction.

## Values
| Value | Description |
| ----- | ----------- |
| `created` | The submission has been created or started, but is not ready to be graded. |
| `submitted` | The submission is ready to be graded. |
| `partially-graded` | Further manual scoring must be undertaken. |
| `fully-graded` | Has been graded and returned to the student. |
| `reclaimed` | The student has un-submitted their work. |
