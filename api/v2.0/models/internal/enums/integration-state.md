# Integration State
An **Integration State** describes the state of an
**[Integration](../integration)**.

The values of this enum are of type `string`.

> This page is under construction.

## Values
| Value | Description |
| ----- | ----------- |
| `requested` | A district has requested an integration with a developer. |
| `inactive` | The developer has accepted the invitation, but the data for this integration is still being prepared. |
| `scheduled` | The data has been prepared, but the integration start date is still in the future. |
| `active` | The integration is live. |
| `disabled` | The integration has been disabled. Users cannot sign in or make API requests.
| `paused` | The sync has been paused by the developer or district. Users can still make API requests. |
| `error` | Currently unused. |
| `pending` | Currently unused. |
