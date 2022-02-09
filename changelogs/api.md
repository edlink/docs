# Edlink API Changelog

This document covers all releases of the Edlink API.

##### 2 September 2021
## Version 1.10.14

- Internal changes.

##### 1 September 2021
## Version 1.10.13

- Also retrieve the support website URL when you load the public details for an application.

##### 1 September 2021
## Version 1.10.12

- Fixed request filtering on V2.

##### 1 September 2021
## Version 1.10.11

- Fixed an issue with Microsoft assignments and added a few sharing rules helper methods.
- Add structured response to pagination decorator.
- Added more Open API documentation.
- Allow creating assignments for a particular section in API v1.
- Bugfixes for creating and updating assignments assigned to a specific Schoology section's students.
- Allow updating assignments to be assigned to a particular section in API V1.

##### 27 August 2021
## Version 1.10.10

- Better logging on failed logins.
- Submissions bug fix.

##### 24 August 2021
## Version 1.10.9

- Internal changes.

##### 24 August 2021
## Version 1.10.8

- Added more UUID validation for better error messages.

##### 24 August 2021
## Version 1.10.7

- Fixed an issue with the V1 events API endpoint.
- Added an email & password sign in method.
- Fixed a couple of issues with assignments.
- Fixed an issue with organization expansion.

##### 15 August 2021
## Version 1.10.6

- Fixed a couple of rules endpoints.
- Filter people by role.
- List child syncs method for new partial sync strategy.
- Adding endpoints for Google launches.
- Fixed the expand sections issue.

##### 10 August 2021
## Version 1.10.5

- Fixed a schoology personalized assignment issue.
- Added organization ancestry back into the events call.
- Fixed the API endpoint to update a personalized assignment.

##### 5 August 2021
## Version 1.10.4

- Handling Google anonymous users login requests.

##### 5 August 2021
## Version 1.10.3

- Enrichment SSO changes.

##### 4 August 2021
## Version 1.10.2

- Fixed middleware to fetch a graph organization without a specified type.
- Fixed an issue with creating new schoology assignments.

##### 30 July 2021
## Version 1.10.1

- Fixed an issue with loading school child courses.
- Few bugfixes in rule creation.
- Fixed a few authentication errors.

##### 26 July 2021
## Version 2.0.2

- Fixed an issue with a few of the Graph API calls where searching for users in a school with a specific role was not functioning correctly.
- Fixed an issue where a person's birthday was also being returned in their `updated_date` property.

##### 23 July 2021
## Version 2.0.1

- Fixed a paging issue when loading district administrators from the Graph API.

##### 21 July 2021
## Version 2.0.0

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

##### 14 July 2021
## Version 1.10.0

- Internal changes.

##### 21 February 2021
## Version 1.9.4

- Fixed an issue where Edlink was trying to send an email to no contacts after a new integration was created.
- Reduced the amount of information exposed publicly about certain applications and integrations to only what was 100% necessary.

##### 24 January 2021
## Version 1.9.3

- Integration analytics endpoint is now significantly faster and contains details about terms and enrollments.
- Internal improvements for sharing rules bugfixes.

##### 14 January 2021
## Version 1.9.2

- SAML added as a login method for OneRoster sources.

##### 6 January 2021
## Version 1.9.1

- Fixed a bug that was preventing courses from being previewed.
- Some User Data API endpoints were not properly observing sharing rules.

##### 3 January 2021
## Version 1.9.0

- Data can now be shared via rules.

##### 13 December 2020
## Version 1.8.5

- Edlink will now pre-handle a several common Microsoft Teams issues.
    - When you try to create an assignment with a title greater than 70 characters, Edlink will throw a `400` error.
    - When you try to update an assignment and set a title greater than 70 characters, Edlink will throw a `400` error.
    - When you try to create an assignment without a due date, Edlink will throw a `400` error.
- A bug has been fixed that was causing an inaccurate `organization.ancestry` array to be returned by the `/api/v1/my/courses` endpoint (and similar endpoints).

##### 21 October 2020
## Version 1.8.4

- Fixed an issue where expired access tokens were not being properly refreshed before making a GraphQL request.
- You can now expand the details about course sections in the `/v1/my/courses` call.

##### 22 September 2020
## Version 1.8.3

- You are now able to filter Graph API data by a number of different parameters.

##### 21 September 2020
## Version 1.8.2

- You can now launch into an integration with your default application parameters already set.
    - This is primarily targeted at use cases such as Microsoft MyApps tiles.
    - While it is not true "SSO", it can streamline the process for teachers and students.
- The Edlink Dashboard will no longer display teams that are marked as `inactive`.
- The sync date will now be returned when you fetch or list enrollments through the Graph API.
- The entity and team IDs will now be properly removed when you fetch details about a single integration by ID.

##### 14 September 2020
## Version 1.8.1

- Listing student submissions from Schoology will now return the entire class, rather than just students who have submitted the item.
    - Students who have not submitted the item will be returned, but most properties will be `null`.
    - This change should bring Schoology more into line with the behavior of other learning management systems.
- The maximum page size on Graph API calls has been increased to 10,000. It was previously 1,000.

##### 9 September 2020
## Version 1.8.0

- Dramatic performance and scalability improvements for the impending back-to-school tsunami.

##### 5 September 2020
## Version 1.7.11

- You will no longer receive student submissions for those students who are "invalid" within our system (i.e. due to a faulty data sync).
- We will now return a `404` error if you attempt to retrieve a submission from an "invalid" student.
- Fixed assignment timezone issues with both Google Classroom and Schoology.
- Fixed an assignment submission bug in Google Classroom.
- Simplified the Google Classroom display date logic. Google Classroom assignments are now automatically marked as "unpublished" when a display date is provided, because Classroom will default to a `PUBLISHED` state otherwise (ignoring display date altogether).
- Made dramatic improvements to performance on calls to retrieve student enrollments through the User Data API.

##### 24 August 2020
## Version 1.7.10

- Brightspace assignments will now properly create a gradebook column.
- Brightspace feedback will now be properly posted to the aforementioned gradebook column.

##### 7 August 2020
## Version 1.7.9

- Clever integrations will no longer try to fetch data from scopes that are unauthorized.
- All LMS requests will now retry up to 5 times upon `5XX` failure.
- Classlink and OneRoster sources will no longer provide `inactive` items in API results.
- Listing enrollments by organization via the Graph API will now return the correct results given enrollments in sub-organizations.
- `person.properties` is now sent with the enrollment call described above.
- We are now properly saving the Clever user role.
- We removed the `district` object from Clever imports.
    - District admins will now receive individual `administrator` enrollments to all of the component schools.
- People will now have an enrollment object that associates them with their Classlink school.
- Google Classroom assignments will now properly default to `description_plaintext` instead of the full HTML `description` property.

##### 2 August 2020
## Version 1.7.8

- The API will no longer import the school district from Clever as this was the only data source for which district information is readily available.
- All sources (even external sources automatically created from Clever or Classlink) will now be tied to a team.
    - External sources will have a team automatically generated for them.
    - External sources may be moved over to the school district's "real" team upon request by an Edlink administrator.
    - Any existing external sources have had a team created for them.
- Schoology API maximum page sizes changed and as a result, some of our imports had triggered sources to become disabled.
- Clever sources will now be disabled when they are disabled in Clever.

##### 27 July 2020
## Version 1.7.7

- Organizations of type `template` will now be returned by default when you call `/my/courses`.
- Blackboard organization states are now decided more intelligently, instead of just relying on Blackboard.
- Technical contacts for the school and developer will now receive a notification email when a new integration is created.
- `Events` will no longer be generated for integrations that are paused.

##### 14 July 2020
## Version 1.7.6

- Made significant performance improvements to API call to list accounts by application & email address (for the SSO routing process).
- The Brightspace sync process will assign more accurate user roles at the system level.
- User access tokens are now invalidated (paused) when an integration is disabled for any reason. They are reactivated if an integration is reenabled.
- Graph access tokens are now invalidated (paused) when an integration is disabled for any reason. They are reactivated if an integration is reenabled.
- Several new email notifications are now available:
    - Developers will receive an email when an integration has been requested.
    - Schools will receive an email when their integration has been approved.
    - Schools and developers will receive an email when a scheduled integration goes live.
- Classes synced from OneRoster will now include the `identifier` property in the `properties` object, if it is available.
- `Provider` objects will now contain a `help` object that may contain a series of configuration help videos.

##### 7 July 2020
## Version 1.7.5

- Google Classroom will now sync archived and provisioned courses.
- A new endpoint was added to retrieve basic analytics about an integration. You can retrieve the number of schools, courses, and people shared by the school district.
- Fixed a bug with the Microsoft Teams sync where teachers would also be enrolled as students in Edlink.
- The endpoint to list your application's integrations now follows standard pagination rules and allows for the `$first`, `$after`, `$last`, and `$before` parameters.

##### 7 July 2020
## Version 1.7.4

- `application/x-www-form-urlencoded` requests will now be accepted for all requests in addition to the standard JSON body type.
- Several new properties have been added to the `/my/profile` user data API request.
- Fixed a bug that caused Microsoft submission scores to be returned in an incorrect format.
- Improved permissions handling for Graph API endpoints.
- Two new endpoints have been added to allow you to retrieve terms (grading periods) through the User Data API.

##### 7 July 2020
## Version 1.7.3

- Blackboard, Canvas, Schoology, and Brightspace custom URLs are now better able to handle trailing slashes or improper URL formats.
- General improvements to OneRoster sync.
    - The OneRoster organization identifier is now available as `organization.properties.identifier`.
- The Canvas sync process will now handle some rather unusual edge cases with regard to enrollments.
    - There can now be multiple enrollments between a user and an organization.
    - There can be multiple enrollments *of the same enrollment type* between a user and an organization (yes, for some reason this happens in practice).
- Although our database will now sync invalid items (e.g. an `enrollment` with no corresponding `person`), these items will not be returned through our API.

##### 25 June 2020
## Version 1.7.2

- Schoology assignment dates (e.g. due date, display date) will now correctly adjust for the time zone.

##### 24 June 2020
## Version 1.7.1

- All cookies are now set to `SameSite=true` and `Secure`.
- The `/my/profile` call will now optionally return expanded data for the person's `Source`, `Provider`, `District`, and `Integration`.

##### 24 June 2020
## Version 1.7.0

- Microsoft users will now be imported with the correct system-level role.
- Fixed a bug in Microsoft submission grading that would have prevented the API from submitting a grade of "0".
- All API responses will now contain the HTTP Strict Transport Security (HSTS) header.
    - You were not previously able to make non-HTTPs requests, but this header was not present.
- People may now contain a properties object which may contain LMS-specific properties.
- Organizations may now contain a properties object which may contain LMS-specific properties.
- Major improvements to the LMS sync process.
    - Targeted updates can be made on-the-fly for more timely data syncing.
- Major internal changes have been made to the Events API.
    - Externally, the API is very slightly different.

##### 31 May 2020
## Version 1.6.3

- Fixed a bug that was preventing the proper import of data from Brightspace. Certain organizations would not have their ancestry properly set, which would cause a number of errors later down the road (e.g. they would not appear when you asked to list a user's courses).
- Fixed a bug with listing or fetching assignments from Brightspace. Items with no availability data were not being handled properly.
- Properly processing Brightspace submissions with multiple attempts.
- Force submissions method implemented for Schoology.
- Fixed a bug that prevented initial login webhooks from firing properly.
- Fixed a bug that was causing Schoology assignments to fail to create if they did not include a due date.
- Improvements to Brightspace assignments, submissions, and grades.

##### 26 May 2020
## Version 1.6.2

- Added a new endpoint to retrieve details about a single integration.
- Switched to updated entities table which includes far more detailed information.
    - All entities will now include their full address and NCES IDs.

##### 26 May 2020
## Version 1.6.1

- Added a new endpoint to the Graph API to list the schools that are ancestors to the requested organization.

##### 25 May 2020
## Version 1.6.0

- Added webhook functionality.
    - Webhooks can be configured on your application page.
    - Webhooks will be attempted up to 10 times (with exponential time decay) in the event of failure.
- Added first two webhook events.
    - A webhook can be fired whenever a user signs into your application.
    - A webhook can be fired whenever a user has signed into your application for the first time.

##### 25 May 2020
## Version 1.5.3

- Added a new endpoint to retrieve details about a user's data source.
    - The endpoint can be found at `/v1/my/source` and contains details about the source, as well as the provider application.
- Fixed a bug where whitespace was improperly handled within users' names in Canvas.

##### 13 May 2020
## Version 1.5.2

- Fixed several bugs related to Blackboard submissions and grades.
    - Assignments are now properly deleted from Blackboard.
- Fixed a bug where Blackboard refresh tokens were improperly saved, as apparently they can change.
- The Blackboard refresh process now happens without a time buffer because Blackboard will not issue new access tokens until the very moment that the old one is expired (they have no issue changing the refresh token every time though, the *exact opposite* of what is supposed to happen) ¯\\\_(ツ)\_/¯.
- Improved the Moodle import with the help of the new Moodle plugin.

##### 11 May 2020
## Version 1.5.1

- Fixed a login bug with anonymous Clever users who initiate the login process from the developer's application (as opposed to Clever Library).
- Made improvements to the Moodle Sync and released a new version of the Edlink Moodle plugin.
- Launch context is now available as a part of the OAuth 2.0 response when launching from an LTI application.
    - Launch context includes the organization (e.g. course) in which the LTI application was opened.
    - It also includes one or more enrollment objects that relate the user to the organization.
    - Users are prevented from launching within contexts to which you (the developer) were not granted access by the school admin.
- A bug with Schoology LTI launch was fixed. Schoology LTI user IDs are different from their standard user IDs.

##### 4 May 2020
## Version 1.5.0

- Changes were made to the organizations data model.
    - `street_address`, `unit_number`, `city`, `state`, `zip`, `website`, and `banner_url` have been removed.
    - Address information (when available) will now be contained exclusively on the organization's `Entity` object.
    - Organizations now have a new property called `state` which indicates the organization's lifecycle state.
    - At present, valid organization states are: `template`, `upcoming`, `inactive`, `active`, `completed`, and `archived`.
- Performance improvements were made to the Canvas sync. Integrations should now be up to 10 times faster.

##### 10 April 2020
## Version 1.4.2

- Added an additional method to fetch Canvas submissions by ID.
- Added support for teacher submission feedback for Canvas.
- Added support for teacher submission feedback for Schoology.
- Better support for Microsoft Teams assignment submissions / grades.
- Better support for Google Classroom assignment submissions / grades.
- Google Classroom now requests an additional permission when teachers and students sign on for the first time.

##### 10 April 2020
## Version 1.4.1

- Made improvements to the automatic entity matching system.
- Expanded entities to provide array types for standard ID numbers.
    - Some systems have duplicate entries for schools.
    - Sometimes schools are combined or merged and we wish to preserve both numbers.

##### 8 April 2020
## Version 1.4.0

- Dramatically simplified the permissions structure for both schools and developers.
    - The create, update, and delete permissions have been merged for each resource type into a single `write` type.
    - Read-only permissions remain the same across the board.
    - Scoped and unscoped permissions have been merged for clarity (and because they were largely redundant).

##### 7 April 2020
## Version 1.3.3

- Added `StudentViewEnrollment` type handler for Canvas.
- Adjusted the internal expiration dates on source access tokens to provide a longer buffer. Access tokens are now refreshed earlier than their expiration date.
- Additional endpoints were added to fetch various enrollment types for individual users requesting information about their organizations.
    - The endpoint has been generalized to `/:organization_type/:organization_id/:enrollment_type`.
- Updated the Canvas sync for performance improvements and to filter out unnecessary courses and enrollments.
- Added a mechanism to activate scheduled integrations.
- Both developers and school admins will now receive an email confirmation when an integration is created.
    - Parties will receive a second email when scheduled integrations are activated.
- Some internal improvements were made with regard to the expiry of events and requests, as per our data retention policy.

##### 30 March 2020
## Version 1.3.2

- Google Classroom assignments that have been deleted will now return a 404 error if they are accessed through our API.
    - Google Classroom typically only performs a "soft delete" and still allows items to be accessed.
    - This behavior is unique to their platform, so we will emulate a "hard delete" for API consistency.
- Improvements to API consistency with Schoology and Canvas assignment submissions.

##### 28 March 2020
## Version 1.3.1

- Stable organization entities are now returned with teams and organizations.
- Changed import queueing strategies for improved reliability and scalability.
- There is now a method to cancel queued imports before they begin.

##### 24 March 2020
## Version 1.3.0

- Backward paging is now implemented for the Graph API.
- Integrations now have a status and can be scheduled to start and end at a specific date.
    - Integrations will now have the property `integration_status` which is set to either `inactive`, `active`, `error`, or `disabled`.
    - Integrations will now have the property `integration_start_date` which is an ISO-8601 timestamp.
    - Integrations will now have the optional property `integration_end_date` which is an ISO-8601 timestamp.
    - Attempts to make API calls to inactive sources will result in a `403 Forbidden` error.
- Integrations now have a configuration object of `integration_configuration`. This is unused at present, but in the future may store specific configuration data for your application.
- Canvas email address support has been improved.
- Calls to retrieved other organizations for an authenticated user have been added (e.g. schools).
- All calls to retrieve information about a user's organizations will now include an enrollments array.
    - For example, users may have more than one enrollment to a course as (in some LMS systems) they can be a teacher in one section and a student in another.
- Calls to organizations endpoints will now include information about the real world entity that relates to the object (if available).
    - For example, schools in Canvas or Schoology generally correspond to real-world locations.
    - Entity IDs are stable and can be relied upon for managing school, district, or university objects.
    - They provide a great way to handle schools who are transitioning between two different LMS systems.
- Internal endpoints were added to list, fetch, and manage entities.

##### 24 February 2020
## Version 1.2.1

- The API call to retrieve a team was not returning data in the proper format.

##### 24 February 2020
## Version 1.2.0

- Fixed several endpoints that were not returning the $data property correctly.
- SSO is now largely decoupled from the Dashboard and is self-contained within the API application.
- The `edlink-api-key` header is no longer required if you are making calls using a user or integration access token.
- Classlink and Clever are now able to perform full roster sync.
- Clever Instant Login is now available as an authentication method.
- OneRoster is now available as a data source provider.

##### 17 February 2020
## Version 1.1.2

- Fixed a bug in the password reset process that was preventing the new password from being saved properly.

##### 15 February 2020
## Version 1.1.1

- Made several minor bugfixes.

##### 15 February 2020
## Version 1.1.0

- All endpoints will now return an object with a `$data` property, and potentially information about pagination (when it is applicable).
- You can now configure Clever and Classlink keys on an application.

##### 30 January 2020
## Version 1.0.1

- Fixed a bug that was preventing applications from being created.