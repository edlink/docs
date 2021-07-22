# Term

Terms are Edlink's representation of academic sessions. In essence, they are time periods to which organizations can be attached. Schools may use terms to indicate quarters, semesters, or some other timeframe by which they track their students' performance. In Edlink, any organization (e.g. a course) may be tied to one or more terms. For example, a single course may span all four quarters of the academic year. Each quarter may represent a distinct grading or reporting period. Some organizations may also have just one term, or none at all. Terms are particularly relevant if your application produces graded items that it must report back to the LMS or SIS.

## Properties

| Property | Type | Description |
|---|---|---|
| `id` | UUID | A stable UUID representing this term. |
| `name` | String | The display name of this term. |
| `start_date` | Date | The ISO-8601 date when the term begins. |
| `end_date` | Date | The ISO-8601 date when the term ends. |