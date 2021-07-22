# Source State
A **Source State** describes the state of a
**[Source](../source)**.

The values of this enum are of type `string`.

## Values
| Value | Description |
| ----- | ----------- |
| `inactive` | The source is waiting for its configuration to be validated. This is set automatically if the configuration changes. |
| `active` | The source's initial sync was successful, and the source is scheduled to sync regularly. |
| `error` | The source's validation or sync failed. |
| `disabled` | The source has been disabled manually, and it is not scheduled to sync regularly.
