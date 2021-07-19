Developer applications can only access the data and functions that they are allowed to, as authorized by the school administrator during the integration process. While many of the User Data API permissions are similar to those of the Graph API, they are distinct and cover a wider variety of functionality (e.g. content and gradebook integration). It is important to note that these permissions are **fully separate** from Graph API permissions.

## User Data Permissions

The following list contains all available User Data permissions. You are able to request these permissions from school administrators by [selecting the required permissions](/docs/dashboard/application-permissions-schools) on the Keys & Permissions page in your Dashboard. Attempting to call endpoints with a user token that is unauthorized to access the requested permission will result in a `403 Forbidden` error.

<integration-permissions :scoped="true" />