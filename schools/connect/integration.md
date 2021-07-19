Edlink helps publishers and learning platforms connect to your district's data sources in order to facilitate single sign on (SSO), automatic course rostering, content integration, and grade book syncing. Edlink helps school administrators quickly and safely grant access to sensitive data and provides comprehensive records of all data exchanged.

To meet the needs of your students and staff, Edlink connects to a variety of different learning management systems, SIS systems, and SSO providers that users are already familiar with. The process of connecting each of these different systems will vary slightly, but the general flow is the same. Once a data source (for example, G Suite) is connected to Edlink, you can grant access to specific software vendors. This document details that process.

### Data and Permission Scopes

In order to limit the data and functionality shared with application vendors, Edlink provides administrators with a set of controls. The first control is the ability to limit the amount of data shared with vendors. Instead of sharing data from your entire district, you can limit it to individual schools or even individual courses. The vendor will not be able to access or modify data outside of the scope you set. Teachers and students from outside the selected list will not be able to inadvertently access platforms that they are not intended to use.

Finally, specific vendors may be granted specific permissions. Vendors must specify a list of the default permissions that their application requires. If vendors wish to change these permissions later, your integration will not be broken, but these additional permissions will require your approval. Permissions are generally split into two categories: `read only` and `modify`. This makes it easy for you to discern whether or not a third party application will have the ability to modify data within your source system.

## 1. The Integration Process

The integration process starts when you receive an integration request from a software vendor. Typically, this will be in the form of a hyperlink (URL) or email. While Edlink confirms the identity of all application partners, please be aware of phishing attacks and **only follow links that open to https://ed.link**.

Integration links will be formatted roughly as follows (with a varying code at the end):

`https://ed.link/integrate/78d5dd75-7af5-401a-ac83-18f5e1e7d4f1`

Once you open an integration link, you will see the integration overview screen. This screen is purely informational and contains details about the application, vendor, accepted data sources, and capabilities of the integration. When you're ready, click `Continue With Integration`.

### 2. Creating an Account

The first step in the integration process is to create an administrator account. This account is used to connect and manage connections to your learning management system, G Suite, Microsoft Office 365, etc. Teachers and students will not have to create accounts. *This process is for administrators only.* If you already have an account, you can sign in and continue to the next step.

If you have not already created an account, you will also be prompted to create a new organization for your school or district. Enter the name of your organization and select a short nickname. Please note that nicknames must be at least 3 characters long and must be unique. If you accidentally select a nickname that has already been used, you will receive a warning.

### 3. Connecting a Source

Select the desired source from the dropdown menu and complete the required fields. Edlink connects with a variety of different systems. Each system will vary slightly in the connection process. We have carefully details the steps for each system in its respective article. You can find more information about each system in the left-hand sidebar of this page.

If you have already selected a source, you may simply select it from the list. If you have more than one connected source, they will both be available for selection.

### 4. Reviewing the Requested Permissions

Once your source is connected, you should carefully review the requested permissions. The vendor's required permissions cannot be modified by school administrators at this time. When you have reviewed the permissions, you may click `Create Integration` to proceed.

### 5. You're All Done

That's it - if your integration was successful, you should see a brief confirmation screen. Please note, after your integration has been created, there may be a brief delay before teachers and student can sign into the vendor's platform. This is caused by two factors, and may vary based on the source you've connected, and the software vendor you've granted access to:

1. Edlink requires a few minutes to sync with your data source.
2. The software vendor may require several minutes to sync with Edlink.

Once everything is synced up properly, users can begin to sign into the vendor's platform and enjoy the smooth data sync that Edlink enables!