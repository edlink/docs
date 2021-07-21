# Organization

Organizations are a base class in the Edlink Graph API. Organizations may contain people (through [enrollments](/docs/graph/enrollments)) or they may contain other organizations. In the Graph API, you may access organizations directly, or through a set of aliases that we provide for convenience.

One of the challenges of modeling organizational units in any abstract system is that data sources can vary wildly in their implementations.

## Properties

| Property | Type | Description |
|---|---|---|
| `id` | UUID | A stable UUID representing this integration. |
| `type` | String | The type of this organization (e.g. a course). See the available types below. |
| `name` | String | The display name of this organization. |
| `description` | String | A short description for this organization. |
| `icon_url` | String | A URL to an icon or profile picture for this organization. |
| `state` | String | The state in which the organization is located. |
| `time_zone` | String | The time zone in which the organization is located. |
| `ancestry` | Array | An array of organization UUIDs representing the parents of this organization. |
| `terms` | Array | An array of term UUIDs to which the course belongs. |
| `entity` | Entity | Metadata about the physical entity (e.g. a school building). |
| `source` | Source | Metadata about the source to which this organization belongs. |

## Additional Notes

* Sections are much more common at the post-secondary level (e.g. colleges and universities). They typically represent something like a Monday/Wednesday/Friday or Tuesday/Thursday section, where the professor may be the same, but schedules, teaching assistants, and coursework may vary.
* Edlink V1 does not have an organization type that represents a "catalog course" or "course template" (something that is modeled by the "course" object in Edlink V2 or OneRoster, for example).
* Not all fields will be available for all organizations. For example, while a school may have a street address, a course will not.