# Enrollments

## List Enrollments

### *GET* https://ed.link/api/v2/graph/enrollments

Retrieve a list of all **[Enrollments](../models/external/enrollment)**.

#### Request Parameters

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/enrollments', {
	headers: {
		authorization: `Bearer ${integration_access_token}`
	}
});
```

### Sample Response

```json
{
  "$data": [
    {
      "id": "00000000-0000-0000-0000-000000000000",
      "created_date": "2021-07-13T17:45:27.674Z",
      "updated_date": "2021-07-13T17:45:27.674Z",
      "start_date": null,
      "end_date": null,
      "role": "teacher",
      "primary": null,
      "state": "active",
      "properties": {},
      "person_id": "00000000-0000-0000-0000-000000000000",
      "class_id": "00000000-0000-0000-0000-000000000000",
      "section_id": "00000000-0000-0000-0000-000000000000"
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## Fetch Enrollment

### *GET* https://ed.link/api/v2/graph/enrollments/:enrollment\_id

Retrieve information about a specific **[Enrollment](../models/external/enrollment)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `enrollment_id` | `string` | The UUID of the desired **[Enrollment](../models/external/enrollment)**. |

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/enrollments/00000000-0000-0000-0000-000000000000', {
	headers: {
		authorization: `Bearer ${integration_access_token}`
	}
});
```

#### Sample Response

```json
{
  "$data": {
    "id": "00000000-0000-0000-0000-000000000000",
    "created_date": "2021-07-13T17:45:27.674Z",
    "updated_date": "2021-07-13T17:45:27.674Z",
    "start_date": null,
    "end_date": null,
    "role": "teacher",
    "primary": null,
    "state": "active",
    "properties": {},
    "person_id": "00000000-0000-0000-0000-000000000000",
    "class_id": "00000000-0000-0000-0000-000000000000",
    "section_id": "00000000-0000-0000-0000-000000000000"
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```
