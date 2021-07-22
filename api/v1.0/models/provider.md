# Provider

Edlink stores basic information on each of the data providers to which it connects connects. These data providers may be learning management systems (LMSs), student information systems (SISs), or even other data connectors such as Classlink and Clever. The provider object contains basic metadata about each system, and likely does not need to be used by your application. A reason that you may wish to access this endpoint is to automatically construct a list of the systems to which your product connects.

## Properties

| Property | Type | Description |
|---|---|---|
| `id` | UUID | A stable UUID representing this provider. |
| `application` | String | The internal name of this provider. |
| `name` | String | The formatted name of this provider. |
| `icon_url` | String | A URL to the icon for this provider. |
| `configuration` | JSON | The required configuration parameters to set up a new connection to this provider. |
| `requires_administrator_login` | Boolean | Whether this provider requires an administrator account to activate. |
| `requires_administrator_consent` | Boolean | Whether this provider requires an administrator consent step to activate. |
| `allows_data_sync` | Boolean | Whether this provider allows full roster data syncing. |
| `requires_remote_configuration` | Boolean | Whether this provider can be set up through Edlink or must be configured through an outside platform. |
