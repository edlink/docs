# Classes

> User API v2 is in beta and is subject to change.

## List Classes

### *GET* https://ed.link/api/v2/my/classes

Retrieve a list of **[Classes](../models/external/class)** that the current user is enrolled in. A person may be associated with any number of classes, including zero (e.g. if they're an administrator).

#### Request Parameters

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/my/classes', {
	headers: {
		authorization: `Bearer ${person_access_token}`
	}
});
```

### Sample Response

```json
{
  "$data": [
    {
      "id": "00000000-0000-0000-0000-000000000000",
      "name": "Sample Class",
      "description": null,
      "state": "active",
      "picture_url": null,
      "created_date": "2021-07-13T17:45:27.249Z",
      "updated_date": "2022-01-26T22:44:36.106Z",
      "locale": null,
      "time_zone": null,
      "school_id": "00000000-0000-0000-0000-000000000000",
      "course_id": null,
      "session_ids": [],
      "subjects": [],
      "grade_levels": [],
      "periods": [],
      "properties": {},
      "identifiers": []
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## Fetch A Single Class

### *GET* https://ed.link/api/v2/my/classes/:class_id

Retrieve information about the specific **[Class](../models/external/class)** that the current user is associated with.

#### Request Parameters

| Parameter  | Type     | Description                                                    |
|------------|----------|----------------------------------------------------------------|
| `class_id` | `string` | The UUID of the desired **[Class](../models/external/class)**. |

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/my/classes/00000000-0000-0000-0000-000000000000', {
	headers: {
		authorization: `Bearer ${person_access_token}`
	}
});
```

### Sample Response

```json
{
  "$data": {
    "id": "00000000-0000-0000-0000-000000000000",
    "name": "Sample Class",
    "description": null,
    "state": "active",
    "picture_url": null,
    "created_date": "2021-07-13T17:45:27.249Z",
    "updated_date": "2022-01-26T22:44:36.106Z",
    "locale": null,
    "time_zone": null,
    "school_id": "00000000-0000-0000-0000-000000000000",
    "course_id": null,
    "session_ids": [],
    "subjects": [],
    "grade_levels": [],
    "periods": [],
    "properties": {},
    "identifiers": []
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```