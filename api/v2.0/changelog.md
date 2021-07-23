# Changelog

This document covers all V2 releases of the Edlink API. If you're looking for changes to the V1 system, please visit the [corresponding document](/docs/api/v1.0/changelog).

## Version 2.0.0
#### July 21st, 2021

- Initial release of 2.0.0.
    - We **do not** have plans to deprecate V1 at this time.
    - We will continue to make improvements and fix issues in the V1 API.
- Lexical updates:
    - Organizations have been split into several new types: `Districts`, `Schools`, `Classes`, and `Sections`.
    - V1.0 `Courses` have been renamed to `Classes` to fall more in line with industry expectations.
    - We have added a brand new type `Courses` to represent the concept of a course "template".
        - Courses are designed to capture the concept of "Algebra 1", rather than a specific instantiation of a `class`.
        - Classes differ as they are comprised of teachers and students in a room (i.e. at a specific time).
        - Classes may reference a course.
    - We have added the type `agents` to describe the parent/guardian to student relationship.
    - We have renamed V1.0 `Terms` to V2.0 `Sessions` in order to represent a wider array of time-bound objects.
    - Enrollments are now only between a Person and a corresponding Class.
        - They may optionally include a reference to a `section` which is a group of students within a class.
    - All sources will now have a single `district` object and one or more `school` objects.
        - This was not necessarily the case in V1.0 where this was determined by the LMS that the district used.
    - A number of name changes were made to improve consistency across the API.
- You will now find a reference to the district and zero or more schools on each person object.
    - This replaced the old style of having enrollments connect users to their school or district.
- We have introduced the global role of `district-administrator` as it was a source of confusion to represent all administrators as simply `administrator`.
- People may now have more than one global `role`.
- We have improved the way we handle our event deltas to make them more clear for developers.
- Additional notes:
    - Authentication and authorization have not changed. You can use the same tokens to call V1 and V2 endpoints.
    - At the end of the day, you should receive the same information from V1 as V2, just in a considerably different format.
    - New features like agents or courses will not be available through the V1 API.