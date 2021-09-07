# Source
A **Source** is a school's data source connected to Edlink. It can be a Learning Management System, School Information System, or Single Sign-On provider.

> This page is under construction.

## Properties
| Property | Type | Description |
| -------- | ---- | ----------- |
| `id` | `string` | The UUID for the object.<br/>**[$filter operators](../../../../guides/v2.0/filtering-results):** `equals` `in` `not in` |
| `created_date` | `Date` | When the object was first seen by Edlink. |
| `updated_date` | `Date` | When the object was last changed in Edlink. |
| `state` | **[`SourceState`](enums/source-state)** | The state of the source.
| `name` | `string` | The name of the object. |
| `configuration` | `object` | The configuration for the source. Fields will differ based on the associated **[Provider](provider)** defined by `provider_id`. |
| `properties` | `object` | Non-standard properties that may be of interest to the developer. |
| `provider_id` | `string` | The UUID of the associated **[Provider](provider)**. |
| `team_id` | `string` | The UUID of the **[Team](team)** that owns the source. |
