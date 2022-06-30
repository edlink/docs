# Classes

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

## List Sections in a Class

### *GET* https://ed.link/api/v2/my/classes/:class\_id/sections

Retrieve a list of **[Sections](../models/external/section)** associated with the specified **[Class](../models/external/class)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `class_id` | `string` | The UUID of the desired **[Class](../models/external/class)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/my/classes/00000000-0000-0000-0000-000000000000/sections', {
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
      "created_date": "2021-07-13T17:45:27.645Z",
      "updated_date": "2021-07-13T17:45:27.645Z",
      "name": "Section 3",
      "description": null,
      "picture_url": null,
      "state": "active",
      "locale": "en",
      "time_zone": "America/Chicago",
      "properties": {},
      "periods": [
        "06"
      ],
      "class_id": "00000000-0000-0000-0000-000000000000"
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## List a Class's Enrollments

### *GET* https://ed.link/api/v2/my/classes/:class\_id/enrollments

Retrieve a list of **[Enrollments](../models/external/enrollment)** associated with the specified **[Class](../models/external/class)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `class_id` | `string` | The UUID of the desired **[Class](../models/external/class)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/my/classes/00000000-0000-0000-0000-000000000000/enrollments', {
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

## List a Class's People

### *GET* https://ed.link/api/v2/my/classes/:class\_id/people

Retrieve a list of **[People](../models/external/person)** associated with the
specified **[Class](../models/external/class)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `class_id` | `string` | The UUID of the desired **[Class](../models/external/class)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/my/classes/00000000-0000-0000-0000-000000000000/people', {
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
      "created_date": "2021-07-13T17:45:39.937Z",
      "updated_date": "2021-07-13T17:45:39.937Z",
      "first_name": "George",
      "middle_name": "Oscar",
      "last_name": "Bluth",
      "display_name": "Gob Bluth",
      "picture_url": "https://static.wikia.nocookie.net/arresteddevelopment/images/7/79/GOB_on_segway.jpg",
      "roles": [
        "student"
      ],
      "email": "gob.bluth@example.com",
      "phone": "12345556789",
      "locale": "en",
      "time_zone": "America/Los_Angeles",
      "graduation_year": 1996,
      "grade_levels": [ "PS" ],
      "demographics": {},
      "properties": {},
      "district_id": "00000000-0000-0000-0000-000000000000",
      "school_ids": [ "00000000-0000-0000-0000-000000000000" ]
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## List a Class's Teachers

### *GET* https://ed.link/api/v2/my/classes/:class\_id/teachers

Retrieve a list of **[People](../models/external/person)** with the [`teacher` role](../models/external/enums/role) associated with the
specified **[Class](../models/external/class)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `class_id` | `string` | The UUID of the desired **[Class](../models/external/class)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/my/classes/00000000-0000-0000-0000-000000000000/teachers', {
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
      "created_date": "2021-07-13T17:45:39.937Z",
      "updated_date": "2021-07-13T17:45:39.937Z",
      "first_name": "George",
      "middle_name": "Oscar",
      "last_name": "Bluth",
      "display_name": "Gob Bluth",
      "picture_url": "https://static.wikia.nocookie.net/arresteddevelopment/images/7/79/GOB_on_segway.jpg",
      "roles": [
        "teacher"
      ],
      "email": "gob.bluth@example.com",
      "phone": "12345556789",
      "locale": "en",
      "time_zone": "America/Los_Angeles",
      "graduation_year": 1996,
      "grade_levels": [ "PS" ],
      "demographics": {},
      "properties": {},
      "district_id": "00000000-0000-0000-0000-000000000000",
      "school_ids": [ "00000000-0000-0000-0000-000000000000" ]
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## List a Class's Students

### *GET* https://ed.link/api/v2/my/classes/:class\_id/students

Retrieve a list of **[People](../models/external/person)** with the [`student` role](../models/external/enums/role) associated with the
specified **[Class](../models/external/class)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `class_id` | `string` | The UUID of the desired **[Class](../models/external/class)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/my/classes/00000000-0000-0000-0000-000000000000/students', {
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
      "created_date": "2021-07-13T17:45:39.937Z",
      "updated_date": "2021-07-13T17:45:39.937Z",
      "first_name": "George",
      "middle_name": "Oscar",
      "last_name": "Bluth",
      "display_name": "Gob Bluth",
      "picture_url": "https://static.wikia.nocookie.net/arresteddevelopment/images/7/79/GOB_on_segway.jpg",
      "roles": [
        "student"
      ],
      "email": "gob.bluth@example.com",
      "phone": "12345556789",
      "locale": "en",
      "time_zone": "America/Los_Angeles",
      "graduation_year": 1996,
      "grade_levels": [ "PS" ],
      "demographics": {},
      "properties": {},
      "district_id": "00000000-0000-0000-0000-000000000000",
      "school_ids": [ "00000000-0000-0000-0000-000000000000" ]
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```
