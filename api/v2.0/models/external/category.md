# Category
A **Category** is a container for **[Assignments](assignment)**, typically visible through the gradebook interface of an LMS.

## Properties
| Property       | Type     | Description                                                  |
|----------------|----------|--------------------------------------------------------------|
| `id`           | `string` | The UUID for the object.                                     |
| `created_date` | `Date`   | When the object was created in the source.                   |
| `updated_date` | `Date`   | When the object was last updated in the source.              |
| `title`        | `string` | The title of the category.                                   |
| `weight`       | `number` | The weight of the category when calculating grades.          |
| `drop_lowest`  | `number` | The number of lowest scores to drop when calculating grades. |
| `position`     | `number` | The position of the category relative to the others.         |
