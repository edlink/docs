# Role
A **Role** describes a **[Person](../person)**'s role or duty 
within a **[Class](../class)** or **[District](../district)**. 
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
| `observer` | Someone who is observing the class, but not participating. |
| `parent` | A parent. |
| `guardian` | A guardian. |
| `ta`<sup>&dagger;</sup> | A teaching assistant or grader. |
| `aide`<sup>&dagger;</sup> | Someone who provides assistance to a student, such as a sign language interpreter. |
| `designer`<sup>&dagger;</sup> | Someone who can create or modify class content within the source system. |

<sup>&dagger; These values are uncommon.</sup>

## OneRoster Role Mappings
Integrations made with a OneRoster-compatible source will be mapped to Edlink roles according to this table.
 
| OneRoster Role | Edlink Role |
| -------------- | ----------- |
| `administrator` | `administrator` |
| `aide` | `aide` |
| `guardian` | `guardian` |
| `invigilator` | `teacher` |
| `parent` | `parent` |
| `proctor` | `teacher` |
| `relative` | `guardian` |
| `student` | `student` |
| `teacher` | `teacher` |