# Agent
An **Agent** describes the relationship between two people, and is typically used to represent a connection between a
student and their parent or guardian. If a provider supports emergency contacts, this is typically how they are
represented in Edlink.

## Properties
| Property | Type | Description |
| -------- | ---- | ----------- |
| `id` | `string` | The UUID for the object. |
| `relationship` | **[`Relationship`](enums/relationship)** | The relationship between the observer and the target. |
| `properties` | `object` | Non-standard properties that may be of interest to the developer. |
| `observer_id` | `string` | The UUID of the **[Person](person)** who acts as the observer in the relationship. Typically, this is a parent or guardian. |
| `target_id` | `string` | The UUID of the **[Person](person)** who acts as the target in this relationship. Typically, this is a student.

## JSON Example
```json
{
  "id": "00000000-0000-0000-0000-000000000000",
  "relationship": "parent",
  "properties": {},
  "observer_id": "00000000-0000-0000-0000-000000000000",
  "target_id": "00000000-0000-0000-0000-000000000000"
}
```
