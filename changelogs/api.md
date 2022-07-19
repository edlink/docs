# Edlink API Changelog

##### July 19th, 2022

- Added Adult Learning and Continued Learning grade levels to our grade level enum.

##### July 18th, 2022

- Enabled custom transformations.
- Fixed a meta API call that was used by the dashboard to list matches for a given entity.
- Added `school_id`, `course_id`, and `session_ids` as fields that can be overridden for a class.
- Enabled RapidIdentity as a top-level provider in Edlink.
- Fixed an issue that was resulting in an error when you specified a `$fields` query parameter and the result was an empty array.
- Added an endpoint to list integrations by source.
- Fixed an issue with the `/v1/my/profile` call for users outside of the United States region.

##### July 15th, 2022

- Fixed an issue where a school's profile picture was not being returned in some v1 API calls.
- Added support for Moodle LTI 1.3 SSO.
- Fixed a Canvas attachment issue where the API request could fail if the description was null.
- Enabled outbound request logging for v2 user endpoints (to match v1 support of this feature).
- Fixed an issue where materializations would fail due to an override that would point to an object that no longer exists.
- Added endpoints to retrieve staged changes for a sync (prior to the changes being flushed).

##### July 13th, 2022

- Fixed an error that would cause an API request to hang on the `/api/v1/organizations/:id` call when you sent an invalid organization ID.
- Improved the visual style of attachments added to Canvas assignments.
- Improved the error message users receive when they attempt to create a category in a Google Classroom class that does not exist upstream.
- Added validation for CSV sources.
- Fixed a sync error that was causing some Microsoft jobs to fail.

##### July 12th, 2022

- Fixed a couple of issues in the LTI 1.3 launch process.
- Added support for Canvas submission extensions.
- Corrected a time zone issue with some Schoology assignment due dates.
- Improved the "assignment not found" error from Canvas.

##### July 11th, 2022

- Restored proper error messages for invalid routes in API v2.
- When searching through objects for sharing rules, search is now case-insensitive.
- Teacher names are now expanded to be human-readable in the sharing rules UI.

##### July 8th, 2022

- Fixed a number of issues with our new sharing rule preview system (codenamed `Blink`).

##### July 7th, 2022

- Added a number of endpoints to support the retrieval of matches coming from our data enrichment engine.
    - You can now manually add or remove matches if they are incorrect.
- Fixed a bad database query for LTI 1.3 launching into our Toronto region.
- Fixed an issue where we were accidentally rematerializing some paused syncs.
- Fixed an issue with Microsoft assignment attachments in API v2.

##### July 6th, 2022

- Increased support for Clever admins and contacts.

##### July 5th, 2022

- You can now make roster requests against a person in the v2 user API, even if that person has invalid LMS tokens (e.g. because you impersonated them).
    - This brings v2 into line with v1.
- Provide additional details in the API response when you receive a 500 error from Edlink.

##### July 2nd, 2022

- Improved our Blackboard validation function to better understand if the source has been configured correctly.
- Added support for agents (i.e. parental contacts) in Google Classroom.
- Fixed our autofill defaults feature for Schoology in API v2.
- Added several new warning / error codes for situations that can arise around Microsoft attachments.

##### June 30th, 2022

- Improved our logic that deals with Schoology rate limits to make faster requests (on average).

##### June 24th, 2022

- Fixed a few issues related to assignment attachment support in Schoology and Canvas.

##### June 23th, 2022

- Properly parse OneRoster course subject codes during syncs.
- Added a number of new identifiers across almost all supported systems.
    - You can find these identifiers (when they are available) in the `entity.identifiers` array.

##### June 21th, 2022

- You can now see your position in the queue when you're waiting to preview a sharing rule.
- Added support for agents (e.g. parental relationships) in Schoology.
- Changed the URL structure for our LTI 1.3 configuration JSON / JWK endpoints.

##### June 17th, 2022

- Released our new system for previewing sharing rules (codenamed `Blink`).
    - This should offer a way faster and more accurate experience for creating sharing rules.
    - It takes into account transformations and overrides, which our old system did not.

##### June 16th, 2022

- Improved OneRoster sync performance.

##### June 13th, 2022

- Released LTI 1.3 support for launches in Canvas, Blackboard, and Brighspace.

##### June 3rd, 2022

- Improved error message when you send an invalid session_id while creating an assignment.
- Added a warning message in v2 when the autofill features fills out a missing field for you.

##### June 2nd, 2022

- Fixed a bug that was preventing standard API requests against paused integrations.
    - Note, only `disabled` integrations should return an error.
- Fixed an issue in Schoology & Canvas assignments where we were not properly handling individualized assignments.

##### May 30th, 2022

- Added a set of mirror endpoints for the Clever v2.1 API.
- Entity identifiers will now be returned in API v1.
    - They were previously only returned in v2.

##### May 27th, 2022

- Fixed an issue with Canvas assignment `points_possible` not updating correctly.
- Fixed an issue with listing integrations when you have none to list.
- Improved some sync code to map things to only `CEDS` grade levels.
- Fixed our import of Clever student grade levels and class subjects.
- Fixed an API v1 issue preventing submission feedback from correctly submitting to Brightspace.

##### May 24th, 2022

- Updated v2 Google draft submission grade behavior to match v1.
- Added `gender_identity` to the list of valid person overrides.
- Fixed a couple of issues related to grading LTI-based assignments in Canvas.
    - Canvas only allows LTI grading of LTI assignments so a special case needed to be implemented.

##### May 20th, 2022

- Removed our `properties.identifiers` backwards compatibility in lieu of the new `identifiers` array.
    - Any affected clients were transitioned to the new structure.
- Person races array in v2 will now default to an empty array instead of `null`.
- Fixed an issue that affected the $expand parameter's handling of array expansions.

##### May 19th, 2022

- Fixed an issue with the login history method that was caused by a person being unshared or deleted from an upstream source.
- Fixed an issue that prevented changes to the identifiers arrays from being staged.

##### May 17th, 2022

- Updated Google Classroom integration to support multiple attachment objects on an assignment.
- We're now syncing various new demographics fields.
- Added support for alternative login URLs for unusual Schoology setups.

##### May 15th, 2022

- Released broader 2FA support for Edlink dashboard users.
- Newly created applications will automatically have an LTI 1.3 JWK created for them.
- Application `anonymous_providers` is now an array of provider UUIDs and not a boolean.
    - This will be more flexible as we expand support for anonymous providers.

##### May 11th, 2022

- Introduced multiregion support for compliance with data sovereignty laws.
    - With this, we released our first region, Toronto.

##### May 10th, 2022

- Fixed an issue with Clever anonymous user logins.

##### May 6th, 2022

- Created an `/api/v2/my/source` endpoint for loading information about your own district and LMS.
- Fixed some issues with Canvas assignment states in API v2.
- Created a Clever compatibility block to make any data backwards compatible with what comes out of Clever API v2.1.

##### May 4th, 2022

- Clever sync will now include contacts.
- Fixed an issue with Canvas assignment grading types in v2.
- Added match introspection capabilities.

##### April 29th, 2022

- Improvements to our data enrichment matching algorithm.

##### April 22nd, 2022

- Added `starts with` and `ends with` to `course_code` sharing rule field.
- Added support for Clever roster sync lite rostering.
    - Previously, we only supported full roster syncing with Clever and Clever library.

##### April 20th, 2022

- Added kebab case and phone number formatting transform blocks.

##### April 18th, 2022

- Significantly expanded our Clever identifier syncing.
- Performance improvements for when you use the `$expand` parameter.

##### April 13th, 2022

- Edlink will no longer share observer enrollments to classes if we are not sharing guardians with your application.
- Released an intial version of integration overrides.
    - You can manually insert, update, and delete data from the Edlink dataset without it being clobbered by future syncs.

##### April 8th, 2022

- Added `rural_residency` permission.

##### April 3rd, 2022

- Added a privacy block that can conceal certain fields in the dataset if they are unused by the developer.

##### March 28th, 2022

- Simplified the Edlink permission to give broader permissions around entities and more specific permissions around user data.
- Expanded the number of available demographic fields.

##### March 24th, 2022

- Fixed an issue with Brightspace assignment submission types.

##### March 20th, 2022

- Edlink will now properly update source states to reflect their respective Clever / Classlink integration states.

##### March 16th, 2022

- Fixed a couple of issues with the API endpoints to create transformations.
- Released a number of improvements to the data enrichment algorithm.

##### March 10th, 2022

- Implemented the correct Microsoft submissions lifecycle in API v2.
- Fixed a couple of issues related to Brightspace assignment submissions.

##### March 7th, 2022

- Made improvements to our OneRoster CSV sync.
    - These improvements are mostly dealing with the scale of massive districts (250k+ users).

##### February 28th, 2022

- Switched the `PROVISIONED` state in Google Classroom to map to `inactive` in Edlink.

##### February 13th, 2022

- V1 endpoints will now log outbound requests made from Edlink to the LMS.

##### January 22nd, 2022

- Beta release of user API v2.

##### January 7th, 2022

- Beta release of new data enrichment engine (codenamed `Tango`).
- Fixed a couple of LTI launch issues.

##### December 29th, 2021

- Fixed a bug in assignee aliasing.
- Added `/my/classes/:id/enrollments` endpoint.

##### December 15th, 2021

- Beta release of Graph API v2.
- Fixed an issue that was causing Blackboard syncs to fail after an hour.

##### December 3th, 2021

- Fixed a few Classlink syncs that were not comforming to the OneRoster specification.
- Corrected some empty string situations in Classlink syncs.
- Fixed an issue with Brightspace user roles.

##### November 30th, 2021

- Set Brightspace default points possible.
- Properly parse person roles in `/v1/my/profile`.
    - This isn't strictly a feature in our documentation, but we wanted it to be available nonetheless.
- Fixed some missing agent roles in the Bromcom SIS sync.

##### November 24th, 2021

- Reenabled Edlink SFTP provider.

##### October 21st, 2021

- Minor change to Illuminate Education to add addtional standards info.

##### October 17th, 2021

- Assign a default grading period and category to Schoology assignments.
- Send a 200 instead of a 204 for delete assignment endpoint.

##### October 15th, 2021

- Fixed an Illuminate Education issue (race condition with token refresh).
- Expanded our demographics models.

##### October 12th, 2021

- Send a 200 instead of a 204 for delete submission endpoint.

##### October 11th, 2021

- Google assignment submission can now contain a URL.

##### October 10th, 2021

- Sync classes and enrollments for Clever Library users.

##### October 8th, 2021

- Added Bromcom roster sync support.
- Updated a few OneRoster role mappings.

##### September 29th, 2021

- OneRoster courses will now properly sync subjects.

##### September 28th, 2021

- Added HelloID as a top-level SSO provider.
- Fixed OneRoster subject codes when they don't match CEDS standard.
- Greatly improved Canvas sync speed.

##### September 23th, 2021

- Fixed Clever sync validation.
- Fixed an issue with Moodle login.
- Added support for Clever identifiers and grade levels.

##### September 19th, 2021

- Added a few endpoints to handle sharing rule previews.
- Added GraphQL pagination for Canvas syncs.
- We are now tracking the number of sync attempts in the event that a job fails.

##### September 16th, 2021

- Implemented a cleaner solution for validating Schoology sources with custom URLs.

##### September 15th, 2021

- Patched a v1 submissions list issue in Canvas.

##### September 14th, 2021

- Return enrollment state wherever we retrieve enrollments.
- Add source validation for some additional sources.

##### September 10th, 2021

- Fixed enrollments paging issue.

##### September 9th, 2021

- Fixed an issue with fetching single Schoology submissions.

##### September 8th, 2021

- The `state` parameter is no longer a required parameter for Edlink SSO.

##### September 1st, 2021

- Also retrieve the support website URL when you load the public details for an application.
- Fixed request filtering on v2.

##### August 31st, 2021

- Fixed an issue with Microsoft assignments and added a few sharing rules helper methods.
- Add structured response to pagination decorator.
- Added more Open API documentation.
- Allow creating assignments for a particular section in API v1.
- Bugfixes for creating and updating assignments assigned to a specific Schoology section's students.
- Allow updating assignments to be assigned to a particular section in API v1.

##### August 27th, 2021

- Better logging on failed logins.
- Submissions bug fix.

##### August 24th, 2021

- Added more UUID validation for better error messages.
- Fixed an issue with the v1 events API endpoint.
- Added an email & password sign in method.
- Fixed a couple of issues with assignments.
- Fixed an issue with organization expansion.

##### August 15th, 2021

- Fixed a couple of rules endpoints.
- Filter people by role.
- List child syncs method for new partial sync strategy.
- Adding endpoints for Google launches.
- Fixed the expand sections issue.

##### August 10th, 2021

- Fixed a schoology personalized assignment issue.
- Added organization ancestry back into the events call.
- Fixed the API endpoint to update a personalized assignment.

##### August 5th, 2021

- Handling Google anonymous users login requests.
- Enrichment SSO changes.

##### August 4th, 2021

- Fixed middleware to fetch a graph organization without a specified type.
- Fixed an issue with creating new schoology assignments.

##### July 30th, 2021

- Fixed an issue with loading school child courses.
- Few bugfixes in rule creation.
- Fixed a few authentication errors.

##### July 26th, 2021

- Fixed an issue with a few of the Graph API calls where searching for users in a school with a specific role was not functioning correctly.
- Fixed an issue where a person's birthday was also being returned in their `updated_date` property.

##### July 23rd, 2021

- Fixed a paging issue when loading district administrators from the Graph API.

##### July 21st, 2021

- Initial release of 2.0.0.
    - We **do not** have plans to deprecate v1 at this time.
    - We will continue to make improvements and fix issues in the v1 API.
- Lexical updates:
    - Organizations have been split into several new types: `Districts`, `Schools`, `Classes`, and `Sections`.
    - v1.0 `Courses` have been renamed to `Classes` to fall more in line with industry expectations.
    - We have added a brand new type `Courses` to represent the concept of a course "template".
        - Courses are designed to capture the concept of "Algebra 1", rather than a specific instantiation of a `class`.
        - Classes differ as they are comprised of teachers and students in a room (i.e. at a specific time).
        - Classes may reference a course.
    - We have added the type `agents` to describe the parent/guardian to student relationship.
    - We have renamed v1.0 `Terms` to v2.0 `Sessions` in order to represent a wider array of time-bound objects.
    - Enrollments are now only between a Person and a corresponding Class.
        - They may optionally include a reference to a `section` which is a group of students within a class.
    - All sources will now have a single `district` object and one or more `school` objects.
        - This was not necessarily the case in v1.0 where this was determined by the LMS that the district used.
    - A number of name changes were made to improve consistency across the API.
- You will now find a reference to the district and zero or more schools on each person object.
    - This replaced the old style of having enrollments connect users to their school or district.
- We have introduced the global role of `district-administrator` as it was a source of confusion to represent all administrators as simply `administrator`.
- People may now have more than one global `role`.
- We have improved the way we handle our event deltas to make them more clear for developers.
- Additional notes:
    - Authentication and authorization have not changed. You can use the same tokens to call v1 and v2 endpoints.
    - At the end of the day, you should receive the same information from v1 as v2, just in a considerably different format.
    - New features like agents or courses will not be available through the v1 API.

##### July 14th, 2021

- Internal changes.

##### February 21st, 2021

- Fixed an issue where Edlink was trying to send an email to no contacts after a new integration was created.
- Reduced the amount of information exposed publicly about certain applications and integrations to only what was 100% necessary.

##### January 24th, 2021

- Integration analytics endpoint is now significantly faster and contains details about terms and enrollments.
- Internal improvements for sharing rules bugfixes.

##### January 14th, 2021

- SAML added as a login method for OneRoster sources.

##### January 6th, 2021

- Fixed a bug that was preventing courses from being previewed.
- Some User Data API endpoints were not properly observing sharing rules.

##### January 3rd, 2021

- Data can now be shared via rules.

##### December 13th, 2020

- Edlink will now pre-handle a several common Microsoft Teams issues.
    - When you try to create an assignment with a title greater than 70 characters, Edlink will throw a `400` error.
    - When you try to update an assignment and set a title greater than 70 characters, Edlink will throw a `400` error.
    - When you try to create an assignment without a due date, Edlink will throw a `400` error.
- A bug has been fixed that was causing an inaccurate `organization.ancestry` array to be returned by the `/api/v1/my/courses` endpoint (and similar endpoints).

##### October 21st, 2020

- Fixed an issue where expired access tokens were not being properly refreshed before making a GraphQL request.
- You can now expand the details about course sections in the `/v1/my/courses` call.

##### September 22nd, 2020

- You are now able to filter Graph API data by a number of different parameters.

##### September 21st, 2020

- You can now launch into an integration with your default application parameters already set.
    - This is primarily targeted at use cases such as Microsoft MyApps tiles.
    - While it is not true "SSO", it can streamline the process for teachers and students.
- The Edlink Dashboard will no longer display teams that are marked as `inactive`.
- The sync date will now be returned when you fetch or list enrollments through the Graph API.
- The entity and team IDs will now be properly removed when you fetch details about a single integration by ID.

##### September 14th, 2020

- Listing student submissions from Schoology will now return the entire class, rather than just students who have submitted the item.
    - Students who have not submitted the item will be returned, but most properties will be `null`.
    - This change should bring Schoology more into line with the behavior of other learning management systems.
- The maximum page size on Graph API calls has been increased to 10,000. It was previously 1,000.

##### September 9th, 2020

- Dramatic performance and scalability improvements for the impending back-to-school tsunami.

##### September 5th, 2020

- You will no longer receive student submissions for those students who are "invalid" within our system (i.e. due to a faulty data sync).
- We will now return a `404` error if you attempt to retrieve a submission from an "invalid" student.
- Fixed assignment timezone issues with both Google Classroom and Schoology.
- Fixed an assignment submission bug in Google Classroom.
- Simplified the Google Classroom display date logic. Google Classroom assignments are now automatically marked as "unpublished" when a display date is provided, because Classroom will default to a `PUBLISHED` state otherwise (ignoring display date altogether).
- Made dramatic improvements to performance on calls to retrieve student enrollments through the User Data API.

##### August 24th, 2020

- Brightspace assignments will now properly create a gradebook column.
- Brightspace feedback will now be properly posted to the aforementioned gradebook column.

##### August 7th, 2020

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

##### August 2nd, 2020

- The API will no longer import the school district from Clever as this was the only data source for which district information is readily available.
- All sources (even external sources automatically created from Clever or Classlink) will now be tied to a team.
    - External sources will have a team automatically generated for them.
    - External sources may be moved over to the school district's "real" team upon request by an Edlink administrator.
    - Any existing external sources have had a team created for them.
- Schoology API maximum page sizes changed and as a result, some of our imports had triggered sources to become disabled.
- Clever sources will now be disabled when they are disabled in Clever.

##### July 27th, 2020

- Organizations of type `template` will now be returned by default when you call `/my/courses`.
- Blackboard organization states are now decided more intelligently, instead of just relying on Blackboard.
- Technical contacts for the school and developer will now receive a notification email when a new integration is created.
- `Events` will no longer be generated for integrations that are paused.

##### July 14th, 2020

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

##### July 8th, 2020

- Google Classroom will now sync archived and provisioned courses.
- A new endpoint was added to retrieve basic analytics about an integration. You can retrieve the number of schools, courses, and people shared by the school district.
- Fixed a bug with the Microsoft Teams sync where teachers would also be enrolled as students in Edlink.
- The endpoint to list your application's integrations now follows standard pagination rules and allows for the `$first`, `$after`, `$last`, and `$before` parameters.

##### July 7th, 2020

- `application/x-www-form-urlencoded` requests will now be accepted for all requests in addition to the standard JSON body type.
- Several new properties have been added to the `/my/profile` user data API request.
- Fixed a bug that caused Microsoft submission scores to be returned in an incorrect format.
- Improved permissions handling for Graph API endpoints.
- Two new endpoints have been added to allow you to retrieve terms (grading periods) through the User Data API.
- Blackboard, Canvas, Schoology, and Brightspace custom URLs are now better able to handle trailing slashes or improper URL formats.
- General improvements to OneRoster sync.
    - The OneRoster organization identifier is now available as `organization.properties.identifier`.
- The Canvas sync process will now handle some rather unusual edge cases with regard to enrollments.
    - There can now be multiple enrollments between a user and an organization.
    - There can be multiple enrollments *of the same enrollment type* between a user and an organization (yes, for some reason this happens in practice).
- Although our database will now sync invalid items (e.g. an `enrollment` with no corresponding `person`), these items will not be returned through our API.

##### June 25th, 2020

- Schoology assignment dates (e.g. due date, display date) will now correctly adjust for the time zone.

##### June 24th, 2020

- All cookies are now set to `SameSite=true` and `Secure`.
- The `/my/profile` call will now optionally return expanded data for the person's `Source`, `Provider`, `District`, and `Integration`.
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

##### May 31st, 2020

- Fixed a bug that was preventing the proper import of data from Brightspace. Certain organizations would not have their ancestry properly set, which would cause a number of errors later down the road (e.g. they would not appear when you asked to list a user's courses).
- Fixed a bug with listing or fetching assignments from Brightspace. Items with no availability data were not being handled properly.
- Properly processing Brightspace submissions with multiple attempts.
- Force submissions method implemented for Schoology.
- Fixed a bug that prevented initial login webhooks from firing properly.
- Fixed a bug that was causing Schoology assignments to fail to create if they did not include a due date.
- Improvements to Brightspace assignments, submissions, and grades.

##### May 26th, 2020

- Added a new endpoint to retrieve details about a single integration.
- Switched to updated entities table which includes far more detailed information.
    - All entities will now include their full address and NCES IDs.
- Added a new endpoint to the Graph API to list the schools that are ancestors to the requested organization.

##### May 25th, 2020

- Added webhook functionality.
    - Webhooks can be configured on your application page.
    - Webhooks will be attempted up to 10 times (with exponential time decay) in the event of failure.
- Added first two webhook events.
    - A webhook can be fired whenever a user signs into your application.
    - A webhook can be fired whenever a user has signed into your application for the first time.
- Added a new endpoint to retrieve details about a user's data source.
    - The endpoint can be found at `/v1/my/source` and contains details about the source, as well as the provider application.
- Fixed a bug where whitespace was improperly handled within users' names in Canvas.

##### May 13th, 2020

- Fixed several bugs related to Blackboard submissions and grades.
    - Assignments are now properly deleted from Blackboard.
- Fixed a bug where Blackboard refresh tokens were improperly saved, as apparently they can change.
- The Blackboard refresh process now happens without a time buffer because Blackboard will not issue new access tokens until the very moment that the old one is expired (they have no issue changing the refresh token every time though, the *exact opposite* of what is supposed to happen) ¯\\\_(ツ)\_/¯.
- Improved the Moodle import with the help of the new Moodle plugin.

##### May 11th, 2020

- Fixed a login bug with anonymous Clever users who initiate the login process from the developer's application (as opposed to Clever Library).
- Made improvements to the Moodle Sync and released a new version of the Edlink Moodle plugin.
- Launch context is now available as a part of the OAuth 2.0 response when launching from an LTI application.
    - Launch context includes the organization (e.g. course) in which the LTI application was opened.
    - It also includes one or more enrollment objects that relate the user to the organization.
    - Users are prevented from launching within contexts to which you (the developer) were not granted access by the school admin.
- A bug with Schoology LTI launch was fixed. Schoology LTI user IDs are different from their standard user IDs.

##### May 4th, 2020

- Changes were made to the organizations data model.
    - `street_address`, `unit_number`, `city`, `state`, `zip`, `website`, and `banner_url` have been removed.
    - Address information (when available) will now be contained exclusively on the organization's `Entity` object.
    - Organizations now have a new property called `state` which indicates the organization's lifecycle state.
    - At present, valid organization states are: `template`, `upcoming`, `inactive`, `active`, `completed`, and `archived`.
- Performance improvements were made to the Canvas sync. Integrations should now be up to 10 times faster.

##### April 10th, 2020

- Added an additional method to fetch Canvas submissions by ID.
- Added support for teacher submission feedback for Canvas.
- Added support for teacher submission feedback for Schoology.
- Better support for Microsoft Teams assignment submissions / grades.
- Better support for Google Classroom assignment submissions / grades.
- Google Classroom now requests an additional permission when teachers and students sign on for the first time.
- Made improvements to the automatic entity matching system.
- Expanded entities to provide array types for standard ID numbers.
    - Some systems have duplicate entries for schools.
    - Sometimes schools are combined or merged and we wish to preserve both numbers.

##### April 8th, 2020

- Dramatically simplified the permissions structure for both schools and developers.
    - The create, update, and delete permissions have been merged for each resource type into a single `write` type.
    - Read-only permissions remain the same across the board.
    - Scoped and unscoped permissions have been merged for clarity (and because they were largely redundant).

##### April 7th, 2020

- Added `StudentViewEnrollment` type handler for Canvas.
- Adjusted the internal expiration dates on source access tokens to provide a longer buffer. Access tokens are now refreshed earlier than their expiration date.
- Additional endpoints were added to fetch various enrollment types for individual users requesting information about their organizations.
    - The endpoint has been generalized to `/:organization_type/:organization_id/:enrollment_type`.
- Updated the Canvas sync for performance improvements and to filter out unnecessary courses and enrollments.
- Added a mechanism to activate scheduled integrations.
- Both developers and school admins will now receive an email confirmation when an integration is created.
    - Parties will receive a second email when scheduled integrations are activated.
- Some internal improvements were made with regard to the expiry of events and requests, as per our data retention policy.

##### March 30th, 2020

- Google Classroom assignments that have been deleted will now return a 404 error if they are accessed through our API.
    - Google Classroom typically only performs a "soft delete" and still allows items to be accessed.
    - This behavior is unique to their platform, so we will emulate a "hard delete" for API consistency.
- Improvements to API consistency with Schoology and Canvas assignment submissions.

##### March 28th, 2020

- Stable organization entities are now returned with teams and organizations.
- Changed import queueing strategies for improved reliability and scalability.
- There is now a method to cancel queued imports before they begin.

##### March 24th, 2020

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

##### February 24th, 2020

- The API call to retrieve a team was not returning data in the proper format.
- Fixed several endpoints that were not returning the $data property correctly.
- SSO is now largely decoupled from the Dashboard and is self-contained within the API application.
- The `edlink-api-key` header is no longer required if you are making calls using a user or integration access token.
- Classlink and Clever are now able to perform full roster sync.
- Clever Instant Login is now available as an authentication method.
- OneRoster is now available as a data source provider.

##### February 17th, 2020

- Fixed a bug in the password reset process that was preventing the new password from being saved properly.

##### February 15th, 2020

- Made several minor bugfixes.
- All endpoints will now return an object with a `$data` property, and potentially information about pagination (when it is applicable).
- You can now configure Clever and Classlink keys on an application.

##### January 30th, 2020

- Fixed a bug that was preventing applications from being created.