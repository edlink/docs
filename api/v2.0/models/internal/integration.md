# Integration
An **Integration** is a connection between a **[Source](source)** and an **[Application](application)**.

> This page is under construction.

## Properties
| Property | Type | Description |
| -------- | ---- | ----------- |
| `id` | `string` | The UUID for the object. |
| `created_date` | `Date` | When the object was first seen by Edlink. |
| `updated_date` | `Date` | When the object was last changed in Edlink. |
| `state` | **[`IntegrationState`](enums/integration-state)** | The state of the integration.
| `permissions` | `string[]` | 
| `scope` | **[`IntegrationScope`](enums/integration-scope)** | The scope of the integration.
| `access_token` | `string` | The access token to be used to make API requests relating to this integration's data. |
| `start_date` | `Date` | When the integration period is scheduled to start. |
| `end_date` | `Date` | When the integration period is scheduled to end. |
| `lti_consumer_key` | `string` |
| `lti_shared_secret` | `string` |
| `configuration` | `object` | The configuration for the integration. |
| `locked` | `boolean` |
| `application_id` | `string` | The UUID of the associated **[Application](application)**. |
| `source_id` | `string` | The UUID of the associated **[Source](source)**. |
