# Enrollments

Enrollments represent a relationship between a person and an organization (typically a course or section). People do not have set global roles within Edlink.
Instead, their role is defined within a particular context (e.g. a course). The practical reason for this is that it is common for a user to have more than one
type, depending on the course. For example, a `student` may be a `ta` in one of their courses, or a teacher may be a enrolled in a professional development course
as a `student`.

While enrollments are typically created between people and courses or sections, they can technically exist on any organizational unit. Enrollments to organizations that are not courses or sections can generally be ignored. If you're looking to list enrollments for a particular organization, please see the [organizations](../../graph/organizations) document.

## Properties

| Property | Type | Description |
|---|---|---|
| `id` | UUID | A stable UUID representing this enrollment. |
| `start_date` | Date | The enrollment start date in ISO-8601. |
| `end_date` | Date | The enrollment end date in ISO-8601. |
| `type` | String | The enrollment type as defined below. |
| `person` | Person | The person enrolled. |
| `organization` | Organization | The organization into which they are enrolled. |
| `source` | Source | The data source for this enrollment. |