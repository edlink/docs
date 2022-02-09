# Attempt
An **Attempt** is a record of a **[Person](person.md)**'s
submitted work for an **[Assignment](assignment.md)**.

An example of an **Attempt** might be their submission for
an essay assignment.

## Properties
| Property       | Type           | Description                                |
|----------------|----------------|--------------------------------------------|
| `created_date` | `Date`         | When the object was created in the source. |
| `attachments`  | `Attachment[]` | The attachments for this attempt.          |

# Attachments
Each **Attempt** contains one or more **Attachments**.

## Properties
| Property | Type     | Description                                                              |
|----------|----------|--------------------------------------------------------------------------|
| `type`   | `string` | The type of the attachment. Required.                                    |
| `title`  | `string` | The title of the attachment. Optional, and not supported by all systems. |

Each type of attachment has additional properties that are specific to that type. Read on for more details.

## Attachment Types

### Text
Rich or plain text, such as the body of an essay or a response to a question.

#### Additional Properties
| Property | Type     | Description                                                        |
|----------|----------|--------------------------------------------------------------------|
| `text`   | `string` | The text of the attachment. Required for attachments of this type. |

#### Example
```json
{
  "type": "text",
  "text": "This is the text of the attachment. For example, this could be the body of an essay."
}
```

### Link
A link to some other resource.

#### Additional Properties
| Property | Type     | Description                                                 |
|----------|----------|-------------------------------------------------------------|
| `url`    | `string` | The URL of the link. Required for attachments of this type. |

#### Example
```json
{
  "type": "link",
  "url": "https://ed.link/",
  "title": "Edlink"
}
```

### File
A file uploaded to another system.

> Currently, Edlink does not support the **creation** of `file` attachments, only reading existing `file`s.

#### Additional Properties
| Property           | Type     | Description                                                                              |
|--------------------|----------|------------------------------------------------------------------------------------------|
| `url`              | `string` | The URL to the file. Required for attachments of this type.                              |
| `file_external_id` | `string` | The ID of the file in the external system. Read-only, and only provided by some systems. |
| `size`             | `number` | The size of the file in bytes. Read-only, and only provided by some systems.             |

#### Example
```json
{
  "type": "file",
  "url": "https://ed.link/example.pdf",
  "title": "Some PDF Title",
  "size": 12345
}
```
