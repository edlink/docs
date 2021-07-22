# Person

Students, teachers, parents, and administrators are represented within Edlink as `People`. People do not have a set type or role - instead, they are connected to organizations (e.g. courses) through a set of [enrollments](/api/v1.0/graph/models/external/enrollments).

## Properties

| Property | Type | Description |
|---|---|---|
| `id` | UUID | A stable UUID representing this term. |
| `first_name` | String | The user's first name. |
| `middle_name` | String | The user's middle name. |
| `last_name` | String | The user's last name. |
| `display_name` | String | The user's display name. |
| `picture_url` | String | A URL for the user's profile picture. |
| `birthday` | Date | The user's birthday as an ISO-8601 date. |
| `gender` | String | The user's gender. |
| `email` | String | The user's email address. |
| `phone` | String | The user's phone number. |
| `locale` | String | The user's language preference. |
| `time_zone` | String | The timezone where the user is located. |
| `source` | Source | Metadata about the source that contains this user's account. |