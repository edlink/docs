# Edlink Dashboard Changelog

##### July 7th, 2022

- Added support for adding multiple enrichment sources to a primary source.
    - You can set the priority of these sources to influence how data is merged.
- Added UI to visualize data matches made by our Data Enrichment engine.
    - You can manually delete matches that are incorrect.
    - You can manually assign new matches if you know the corresponding entity in the secondary source.
    - Edlink will provide some details as to how it arrived at a particular match.
- Added a visual progress meter to indicate the loading progress of your Sharing Rule previews.

##### July 1st, 2022

- Sources connected to Flow will now show the destination source ID and name.
- Sources that are tied to a specific application (e.g. Clever, Classlink, and LTI sources) will now show that application in the UI.
- Sources that are tied to a specific application will no longer be selectable during the administrator onboarding flow.

##### June 18th, 2022

- Fixed a bug that caused a bunch of unneccesary network requests after you left the Sharing Rule preview screen.
- Added team ID to the settings page for convenience.
- Added Jobs and Flows tabs to Flow integration UI.
    - You can now preview changes that Flow is going to make to the destination source.
    - You can monitor task progress by clicking on a given Job.
- Fixed a number of page numbering bugs in the integration data browser.
- Fixed a number of bugs with the preview sharing rule UI.

##### June 16th, 2022

- Updated the LTI 1.3 launch link.
    - The old launch link will still work, but it is highly recommended that you use the new one going forward.

##### June 4th, 2022

- Fixed a bug that was preventing administrators from updating their LMS tokens on the source settings page.

##### May 27th, 2022

- Greatly improved the UI to create overrides.
    - You can now insert arbitrary items into the dataset or update existing items.
    - Changes will not be overridden when data sources sync.

##### May 23rd, 2022

- Added a bunch of transformation card templates to show more useful information on the source and integration transformation tabs.
- Fixed a bug with nested properties on the entity details drawer.
- Fixed a number of autocomplete issues with demographics overrides.
- Added a new field that allows administrators to specify alternative login URLs.
    - This is primarily used in situations where teachers and students sign in through different entrypoints.

##### May 20th, 2022

- Added a new set of tabs on the logs page to toggle between geographic regions.
- Added several new autocomplete boxes for the creation of person overrides.

##### May 15th, 2022

- Enabled two-factor authentication.
    - You can set up 2FA for yourself by clicking your name in the bottom-left.
    - On the team page, you can quickly see which team members have 2FA enabled.
- Added a new password strength component.
- You can now separately specify if you want to allow Clever, Google, (etc.) anonymous users.
    - Formerly, it was a single setting to allow / deny anonymous users.

##### May 2nd, 2022

- Fixing issues with Chrome autocompleting certain key fields.
- Added two new types of sharing rules (share by school and share by person).

##### April 17th, 2022

- Added the ability to override data in the integration data browser.
- Fixed a bug that was preventing source settings from saving properly.

##### April 13th, 2022

- Added migrations tab.
    - You can now have Edlink help map IDs from Clever or Classlink to a district's LMS.
    - This makes it easy to migrate districts to an LMS integration without losing existing data.

##### April 10th, 2022

- Added integration transformations UI.

##### March 30th, 2022

- Changed the Clever & Classlink secret key fields to a password type.
- Simplified the integration permissions screen.
- Fixed an issue that was preventing users from selecting text on the request log screen.
- Updated some links to the documentation to point to API V2 by default now, following the release of User API V2.

##### March 25th, 2022

- Changed several UIs to autosave and removed their corresponding save buttons.
    - There is now a "saving" indicator in the bottom right.
- Updated the integration overview page to handle Flows.

##### March 20th, 2022

- Added outbound request visibility to see what requests Edlink is making to the upstream data source.

##### January 29th, 2022

- Changed the style of the "beta" alert banner on the V2 documentation.

##### January 24th, 2022

- Fixed the broken help link on the district admin onboarding flow.

##### January 23rd, 2022

- Updated the OIDC connection JSON URL for LTI 1.3 integrations.

##### January 5th, 2022

- Fixed the broken help link on the district admin onboarding flow.

##### December 15th, 2021

- Fixed a few broken documentation links caused by a URL restructuring a few months back.

##### December 1st, 2021

- Fixed the button to delete an integration (it was previously erroring if you clicked it as a developer).

##### November 20th, 2021

- Added a command palette available with `Ctrl+K` or `CMD+K`.

##### November 17th, 2021

- Fixed a couple of broken links on the account settings, login, and register pages.
- Added the guide documentation panel.
- Added a guide button to every page that needed one.
- Fixed the source validation error message issue.
- Quality of life fixes.
    - Made a few things click-to-copy that were previously annoying to highlight.
    - Integration status is now available and changeable from the header.
    - Added information about the enrichment status of sources / integrations.

##### September 9th, 2021

- The SSO login page will now handle edge cases better (e.g. when no redirect_uri is specified by the developer).
- Fixed a bug in the sharing rules creation UI.
- Added some additional sharing rules options (share by course or course code).

##### August 15th, 2021

- Fixed a bug with enrolllments not appearing in the details pane of the integration data browser.

##### August 12th, 2021

- Fixed a number of small issues and began rework of the sharing rules UI.

##### August 5th, 2021

- There is now a bolt icon that appears next to enriched sources.

##### August 4th, 2021

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

##### April 7th, 2021

- Added a new SSO route for launching when you have a previously saved session cookie.

##### January 24th, 2021

- A number of sharing rules UI updates.
- There were several bugs fixed with the sharing rules autocomplete field.
- The integration data pages (e.g. people, courses, etc.) will now show a full count of the number of available items.

##### January 4th, 2021

- There is now a `Sharing` tab added to the integration settings screen.
- You can define rules by which data will be shared with the developer.

##### October 21st, 2020

- There is a new integration overview page containing relevant details about the given integration.
- This page also includes LTI keys so that LTI launches can be configured in the district's LMS.

##### October 3rd, 2020

- Made improvements to the number of fields upon which you can filter your integration data.
- The request method in request logs will now display the correct value.
- There is now a back button to return to your list of integrations.
- We have added an integration overview page to the dashboard.
    - This page contains details about the integration as well as the source data provider.
    - You may also find the access token and LTI configuration information for this integration, but please be aware that these are extremely sensitive.

##### September 21st, 2020

- You can now resize the "Valid Redirect URIs" field.
- The Edlink Dashboard will no longer display teams that are marked as `inactive`.
- Disabled sources will now have an icon indicating their status in the integration flow.
- Teams will now be sorted in alphabetical order on the teams menu.
- Sources will now be sorted in alphabetical order on the "Manage Sources" page.
- We have added a new page in order to browse your integrations.
- We have added a basic read-only data browser for you to have better visibility into the data that comes from our API.

##### August 24th, 2020

- Fixed a bug that caused imports to double-load if you navigated away from and then back to the imports page.
- Fixed a bug that caused some error messages to appear after switching teams.
- We are no longer requiring administrators to create a team `alias` (nickname) when they are going through the integration onboarding flow.
- The list of integrated schools will now be sorted alphabetically by district name.
- We will no longer show "Clever" or "Classlink" in the integration flow as these will have to be configured externally.
- The integration flow will now filter the dropdown list of acceptable sources based on the developers preferences. Previously, only the landing page was filtering properly.
- The integrate account screen will no longer say "null null" if you have not set your name.

##### August 18th, 2020

- Added a new `Logs` page for developers to inspect detailed information about all requests that flow through our system.
- Integrations will now have the district's `Entity ID` displayed below as well as the provider icon to the left.
- We've simplified the school admin onboarding process further and added additional help videos to make the experience clearer.

##### July 21st, 2020

- Made significant performance improvements to the login page (in particular the routing process whereby users are routed to their school's LMS to authenticate).
- Source configuration forms will now have improved help experiences.

##### July 14th, 2020

- Documentation updates.
- Starting to integration help videos and additional documentation into the source configuration process.

##### July 3rd, 2020

- Documentation fixes.

##### May 13th, 2020

- Documentation updates.
- Removed the `Data Sync Interval` field from the source creation and settings pages. It may be added back in the future as an advanced option, but only served as a source of confusion for administrators.

##### May 4th, 2020

- Updated the SSO login flow to include a more informative error page when your account is not found.
- Fixed several bugs in the integration flow.
- Added new team settings.
    - You can now specify one or more technical email addresses to receive important notifications.
    - You can now specify one or more support email addresses which will be displayed on error pages.
    - You can now specify a website and support website URL for users.
- Added some basic statistics on the source overview page.
- The email address search is now case insensitive.

##### April 30th, 2020

- Fixed a bug with creating a new source via the integrate page when you are a part of multiple teams.

##### April 10th, 2020

- Administrative entity and organization management.

##### April 8th, 2020

- Permissions have been simplified.
- Permissions will now be sorted by type (alphabetically).
    - This change applies on both the integration page, as well as the application configuration page.

##### April 7th, 2020

- New flow added for SSO logins. Users can be directed straight to Clever sign in by sending them to `/sso/login/clever`.

##### March 30th, 2020

- Fixed a couple of dead links in the documentation.
- The documentation menu will now open to the active section upon page load.
- Updated sitemaps to reflect changes to the documentation.
- The SSO login screen will now show the loading icon when waiting for the LMS flow to begin.

##### March 29th, 2020

- Added mobile support for the home page, support page, and documentation.

##### March 28th, 2020

- You can now properly scroll on the SSO Login page when you have too many existing accounts.
- There is now an SSO flow for users who do not use an email address.
- Sitemaps were added for the main site and documentation.
- There is now a button to cancel queued imports before they begin.

##### March 24th, 2020

- Added several pages to browse the data that is imported from a source.
- Fixed an issue with the create team modal.
- Source imports will now be listed in reverse chronological order.
- Internal pages were added for the management of entities.

##### February 24th, 2020

- Fixed an issue where you would be directed to onboarding after logging in (even if you were already onboarded).
- Fixed an issue with accepting invitations during the onboarding flow.
- The onboarding flow will now redirect you if you have already onboarded.
- Fixed an issue where the permissions of a newly invited team member were always set to `read`.
- Fixed an issue where Read / Write members of a team would have no label appear next to their name.
- The integration flow has been better split into discrete steps for simplicity.
- OneRoster is now available as a data source provider on the `Create Source` page.
- The Dashboard no longer functions as a privileged application, in fact it is totally stateless and no longer requires any API keys at all.
- All requests are now routed directly to the Edlink API and are no longer proxied through the Dashboard.
- The backend for the Dashboard has been eliminated entirely.
- Frontend files are now properly gzipped and have a new caching policy.
- The above changes should result in drastic speed improvements.
- The documentation has been updated to reflect a number of changes to the API.

##### February 17th, 2020

- Made some visual updates to the SSO login screen.
- Made some visual updates on the application keys page.

##### February 15th, 2020

- Made requests conform to the new backend `$data` requirement.
- You can now add sources from several new providers.

##### January 31st, 2020

- Updated several documents in the documentation section.
- Moved these change logs into their own section of the documentation.
- Fixed some broken links on the home page.
- Improvements to the Graph API documentation.
- Users can now access their individual account settings by clicking on their name in the header.
- Users can now force sign out of all of their accounts from the account settings page.
- The page will now properly scroll to the top upon navigation.
- GDPR warning banner added.

##### January 7th, 2020

- Fixed a bug on the documentation page that caused the interactivity settings to be visible even when the user was not logged in.
- Corrected a margin issue on documentation pages.
- Updated the link to the Edlink community page.

##### January 6th, 2020

- Initial release of Edlink dashboard.
