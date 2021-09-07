Modeling complex data from a variety of different systems presents its challenges. We aim to model data within our system as faithfully as possible to the source system.
This means that the data structure may vary slightly between different sources. Not all sources provide all data attributes, and not all sources have equivalent layers of
abstraction.

To provide a concrete example: Canvas allows clients to model an arbitrary number of "accounts", which may include schools, departments, and sub-departments.
Within these accounts there are courses, and finally, within courses, are course sections. Users may have enrollments to a course or a course section, and users
may even have more than one enrollment in a single course (e.g. they may be a TA in one section, and a student in another). Contrast this with Schoology, which
requires the client conform to a strict school-course-section structure.

To that end, we have modeled our data in as *abstract* a manner as possible, which allows us to deliver it to you in a variety of different formats and (hopefully)
provides you with exactly what is expected in each case - regardless of what we import from the source system.

## Objects

The Edlink Graph API contains only five core object types.

1. **Integrations** are connections to the schools desired data source. These are the "root" of an individual connection.
2. **Organizations** are an abstract representation of any group of people. For convenience, organizations are split up into schools, courses, course sections, etc.
3. **People** represent users within the platform. They could be administrators, teachers, students, or parents.
4. **Enrollments** are connections between people and organizations. Each enrollment will have a type, such as teacher or student.
5. **Terms** are school grading periods or academic sessions. Typically, a term is tied to a course and can be used to determine whether or not a course is active.

## Organization Types

Organizations within Edlink are further subdivided into several types. While there is no "strict" rule regarding which organization types can be the parent or child of another,
typically data is imported as follows:

| Organization Type | Typical Parent Type | Description |
|---|---|---|
| **District** | None (Integration Root) | A collection of schools. |
| **School** | District or None | A school or campus. |
| **Department** | School | A department within a school (less common within K-12). |
| **Course** | Department or School | A course that is taught at the school. |
| **Section** | Course | Groups of students that are taught by the same teacher. |
| **Group** | Course | Groups of students that may be working on similar projects or discussion threads. |

## Enrollment Types

Enrollment types are further discussed in the [enrollments](/docs/api/v1.0/graph/enrollments) document.
