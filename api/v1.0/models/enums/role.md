# Role

A **Role** describes a **[Person](../person)**'s role or duty 
within a Course or District. 
The values you will receive from our API depend heavily on the type
of provider you're using. For instance, few providers will support the `aide` type.

The values of this enum are of type `string`.

## Values

| Value | Description |
| ----- | ----------- |
| `student` | A student. |
| `district-administrator` | A district-level administrator. |
| `administrator` | A school-level administrator. |
| `teacher` | A teacher. |
| `observer` | Someone who is observing the class, but is not a student. |
| `parent` | A parent. |
| `guardian` | A guardian. |
| `ta`<sup>&dagger;</sup> | A teaching assistant. |
| `aide`<sup>&dagger;</sup> | Someone who provides assistance to a student, such as a sign language interpreter. |
| `designer`<sup>&dagger;</sup> | Someone who adds or edits class content. |

<sup>&dagger; These values are uncommon.</sup>
