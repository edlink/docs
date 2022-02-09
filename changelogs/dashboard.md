# Edlink Dashboard Changelog

This document covers all releases of the Edlink Dashboard.

##### 29 January 2022
## v1.6.7

- Changed the style of the "beta" alert banner on the V2 documentation.
##### 24 January 2022
## v1.6.6

- Fixed the broken help link on the district admin onboarding flow.

##### 23 January 2022
## v1.6.5

- Updated the OIDC connection JSON URL for LTI 1.3 integrations.

##### 5 January 2022
## v1.6.4

- Fixed the broken help link on the district admin onboarding flow.

##### 15 December 2021
## v1.6.3

- Fixed a few broken documentation links caused by a URL restructuring a few months back.

##### 1 December 2021
## v1.6.2

- Fixed the button to delete an integration (it was previously erroring if you clicked it as a developer).

##### 20 November 2021
## v1.6.1

- Added a command palette available with `Ctrl+K` or `CMD+K`.

##### 17 November 2021
## v1.6.0

- Fixed a couple of broken links on the account settings, login, and register pages.
- Added the guide documentation panel.
- Added a guide button to every page that needed one.
- Fixed the source validation error message issue.
- Quality of life fixes.
    - Made a few things click-to-copy that were previously annoying to highlight.
    - Integration status is now available and changeable from the header.
    - Added information about the enrichment status of sources / integrations.

##### 9 September 2021
## v1.5.2

- The SSO login page will now handle edge cases better (e.g. when no redirect_uri is specified by the developer).
- Fixed a bug in the sharing rules creation UI.
- Added some additional sharing rules options (share by course or course code).

##### 15 August 2021
## v1.5.1

- Fixed a bug with enrolllments not appearing in the details pane of the integration data browser.

##### 12 August 2021
## v1.5.0

- Fixed a number of small issues and began rework of the sharing rules UI.

##### 5 August 2021
## v1.4.4

- There is now a bolt icon that appears next to enriched sources.

##### 4 August 2021
## v1.4.3

- Added class state as a property available to use in sharing rules.
- Fixed a few bugs in the creation of sharing rules.
- Slightly changed the visual styles of the administrator onboarding flow.
- Removed the integration ID from the Integrations page (you can now find it by clicking on the integration itself).
- Updated the applications page to the new visual styles.
- Moved the documentation to a new Github repo.
- Account settings is now a modal instead of its own page.
- After going through the administrator onboarding flow, you can now have administrators be redirected to a URL of your choosing.
- Fixed an issue with enrollments not appearing in the details pane of the integration data browser.
- Fixed a few bugs with the logged request viewer.
- Renamed `Imports` to `Syncs`.
- Added page title to the login screen.
- Added some customization options to the team settings page (e.g. setting a primary color).

##### 7 April 2021
## v1.4.2

- Added a new SSO route for launching when you have a previously saved session cookie.

## v1.4.1

- A number of sharing rules UI updates.
- There were several bugs fixed with the sharing rules autocomplete field.
- The integration data pages (e.g. people, courses, etc.) will now show a full count of the number of available items.

## v1.4.0

- There is now a `Sharing` tab added to the integration settings screen.
- You can define rules by which data will be shared with the developer.

## v1.3.2

- There is a new integration overview page containing relevant details about the given integration.
- This page also includes LTI keys so that LTI launches can be configured in the district's LMS.

## v1.3.1

- Made improvements to the number of fields upon which you can filter your integration data.
- The request method in request logs will now display the correct value.
- There is now a back button to return to your list of integrations.
- We have added an integration overview page to the dashboard.
    - This page contains details about the integration as well as the source data provider.
    - You may also find the access token and LTI configuration information for this integration, but please be aware that these are extremely sensitive.

## v1.3.0

- You can now resize the "Valid Redirect URIs" field.
- The Edlink Dashboard will no longer display teams that are marked as `inactive`.
- Disabled sources will now have an icon indicating their status in the integration flow.
- Teams will now be sorted in alphabetical order on the teams menu.
- Sources will now be sorted in alphabetical order on the "Manage Sources" page.
- We have added a new page in order to browse your integrations.
- We have added a basic read-only data browser for you to have better visibility into the data that comes from our API.

## v1.2.17

- Fixed a bug that caused imports to double-load if you navigated away from and then back to the imports page.
- Fixed a bug that caused some error messages to appear after switching teams.
- We are no longer requiring administrators to create a team `alias` (nickname) when they are going through the integration onboarding flow.
- The list of integrated schools will now be sorted alphabetically by district name.
- We will no longer show "Clever" or "Classlink" in the integration flow as these will have to be configured externally.
- The integration flow will now filter the dropdown list of acceptable sources based on the developers preferences. Previously, only the landing page was filtering properly.
- The integrate account screen will no longer say "null null" if you have not set your name.

## v1.2.16

- Added a new `Logs` page for developers to inspect detailed information about all requests that flow through our system.
- Integrations will now have the district's `Entity ID` displayed below as well as the provider icon to the left.
- We've simplified the school admin onboarding process further and added additional help videos to make the experience clearer.

## v1.2.15

- Made significant performance improvements to the login page (in particular the routing process whereby users are routed to their school's LMS to authenticate).
- Source configuration forms will now have improved help experiences.

## v1.2.14

- Documentation updates.
- Starting to integration help videos and additional documentation into the source configuration process.

## v1.2.13

- Documentation fixes.

## v1.2.12

- Documentation updates.
- Removed the `Data Sync Interval` field from the source creation and settings pages. It may be added back in the future as an advanced option, but only served as a source of confusion for administrators.

## v1.2.11

- Several documentation fixes.

## v1.2.10

- Updated the SSO login flow to include a more informative error page when your account is not found.
- Fixed several bugs in the integration flow.
- Added new team settings.
    - You can now specify one or more technical email addresses to receive important notifications.
    - You can now specify one or more support email addresses which will be displayed on error pages.
    - You can now specify a website and support website URL for users.
- Added some basic statistics on the source overview page.
- The email address search is now case insensitive.

## v1.2.9

- Fixed a bug with creating a new source via the integrate page when you are a part of multiple teams.

## v1.2.8

- Administrative entity and organization management.

## v1.2.7

- Permissions have been simplified.
- Permissions will now be sorted by type (alphabetically).
    - This change applies on both the integration page, as well as the application configuration page.

## v1.2.6

- New flow added for SSO logins. Users can be directed straight to Clever sign in by sending them to `/sso/login/clever`.

## v1.2.5

- Fixed a couple of dead links in the documentation.
- The documentation menu will now open to the active section upon page load.
- Updated sitemaps to reflect changes to the documentation.
- The SSO login screen will now show the loading icon when waiting for the LMS flow to begin.

## v1.2.4

- Added mobile support for the home page, support page, and documentation.

## v1.2.3

- You can now properly scroll on the SSO Login page when you have too many existing accounts.
- There is now an SSO flow for users who do not use an email address.
- Sitemaps were added for the main site and documentation.
- There is now a button to cancel queued imports before they begin.

## v1.2.2

- Added several pages to browse the data that is imported from a source.
- Fixed an issue with the create team modal.
- Source imports will now be listed in reverse chronological order.
- Internal pages were added for the management of entities.

## v1.2.1

- Fixed an issue where you would be directed to onboarding after logging in (even if you were already onboarded).
- Fixed an issue with accepting invitations during the onboarding flow.
- The onboarding flow will now redirect you if you have already onboarded.
- Fixed an issue where the permissions of a newly invited team member were always set to `read`.
- Fixed an issue where Read / Write members of a team would have no label appear next to their name.

## v1.2.0

- The integration flow has been better split into discrete steps for simplicity.
- OneRoster is now available as a data source provider on the `Create Source` page.
- The Dashboard no longer functions as a privileged application, in fact it is totally stateless and no longer requires any API keys at all.
- All requests are now routed directly to the Edlink API and are no longer proxied through the Dashboard.
- The backend for the Dashboard has been eliminated entirely.
- Frontend files are now properly gzipped and have a new caching policy.
- The above changes should result in drastic speed improvements.
- The documentation has been updated to reflect a number of changes to the API.

## v1.1.1

- Made some visual updates to the SSO login screen.
- Made some visual updates on the application keys page.

## v1.1.0

- Made requests conform to the new backend `$data` requirement.
- You can now add sources from several new providers.

## v1.0.3

- Updated several documents in the documentation section.
- Moved these change logs into their own section of the documentation.

## v1.0.2

- Fixed some broken links on the home page.
- Improvements to the Graph API documentation.
- Users can now access their individual account settings by clicking on their name in the header.
- Users can now force sign out of all of their accounts from the account settings page.
- The page will now properly scroll to the top upon navigation.
- GDPR warning banner added.

## v1.0.1

- Fixed a bug on the documentation page that caused the interactivity settings to be visible even when the user was not logged in.
- Corrected a margin issue on documentation pages.
- Updated the link to the Edlink community page.

## v1.0.0

- Initial release of Edlink dashboard.
