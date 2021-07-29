# Courses

## List Courses

### *GET* https://ed.link/api/v2/graph/courses

Retrieve a list of all **[Courses](../models/external/course)**.

#### Request Parameters

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/courses', {
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
      "created_date": "2021-07-13T17:45:27.570Z",
      "updated_date": "2021-07-13T17:45:27.570Z",
      "name": "Data Structures & Algorithms",
      "code": "CS 425",
      "grade_levels": [],
      "subjects": [
        "CEDS.21"
      ],
      "properties": {},
      "session_id": "00000000-0000-0000-0000-000000000000",
      "school_id": "00000000-0000-0000-0000-000000000000",
      "district_id": "00000000-0000-0000-0000-000000000000"
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## Fetch Course

### *GET* https://ed.link/api/v2/graph/courses/:course\_id

Retrieve information about a specific **[Course](../models/external/course)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `course_id` | `string` | The UUID of the desired **[Course](../models/external/course)**. |

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/courses/00000000-0000-0000-0000-000000000000', {
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
    "created_date": "2021-07-13T17:45:27.570Z",
    "updated_date": "2021-07-13T17:45:27.570Z",
    "name": "Data Structures & Algorithms",
    "code": "CS 425",
    "grade_levels": [],
    "subjects": [
      "CEDS.21"
    ],
    "properties": {},
    "session_id": "00000000-0000-0000-0000-000000000000",
    "school_id": "00000000-0000-0000-0000-000000000000",
    "district_id": "00000000-0000-0000-0000-000000000000"
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## List a Course's Classes

### *GET* https://ed.link/api/v2/graph/courses/:course\_id/classes

Retrieve a list of **[Classes](../models/external/class)** associated with the
specified **[Course](../models/external/course)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `course_id` | `string` | The UUID of the desired **[Course](../models/external/course)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/courses/00000000-0000-0000-0000-000000000000/classes', {
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
      "created_date": "2021-07-13T17:45:27.685Z",
      "updated_date": "2021-07-13T17:45:27.685Z",
      "name": "Defense Against the Dark Arts",
      "description": null,
      "picture_url": null,
      "grade_levels": [
        "06"
      ],
      "subjects": [
        "CEDS.08"
      ],
      "periods": [
        "1"
      ],
      "state": "active",
      "locale": null,
      "time_zone": null,
      "properties": {},
      "session_ids": [
        "00000000-0000-0000-0000-000000000000"
      ],
      "course_id": "00000000-0000-0000-0000-000000000000",
      "school_id": "00000000-0000-0000-0000-000000000000"
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```
