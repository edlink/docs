# Identifier
Many external objects returned from our API will contain an array of **Identifiers**.

Most frequently, these fields provide State IDs, Student Information System IDs, and additional email addresses associated with a **[Person](person)**.

## Properties

| Property | Type | Description |
| -------- | ---- | ----------- |
| `type` | [`IdentifierType`](enums/identifier-type) | The type of identifier. |
| `value` | `string` | The value of the identifier. |
