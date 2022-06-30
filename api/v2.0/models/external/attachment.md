# Attachment
An **Attachment** is associated with an **[Assignment](assignment)**.
It typically includes supporting info, like files including instructions,
or a link to relevant content that might be useful to the assignee.

## Properties
| Property      | Type     | Description                                                                    |
|---------------|----------|--------------------------------------------------------------------------------|
| `type`        | `string` | The type of the attachment. Required.                                          |
| `title`       | `string` | The title of the attachment. Optional, and not supported by all systems.       |
| `description` | `string` | The description of the attachment. Optional, and not supported by all systems. |

Each type of attachment has additional properties that are specific to that type. Read on for more details.

## Submission Attachment Types

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

