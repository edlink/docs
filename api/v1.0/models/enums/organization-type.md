# Organization Type
In V1.0 of the Edlink API, and organization represents a collection of people.
People are associated with an organization via an enrollment.
The **Organization Type** describes the type of **[Organization](../organization)**.

The values of this enum are of type `string`.

## Values

| Value | Description |
| ----- | ----------- |
| `district` | The top level district. There will be one and only one organization with this type (per integration). |
| `school` | An individual school building within the district. |
| `course` | A collection of students and teachers. This is known as a `class` in V2.0 as well as in the OneRoster standard. |
| `section` | A small group of students or teachers within a course. |