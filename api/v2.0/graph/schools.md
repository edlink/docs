# Schools

## List Schools

### *GET* https://ed.link/api/v2/graph/schools

Retrieve a list of all **[Schools](../models/external/school)**.

#### Request Parameters

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/schools', {
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
      "created_date": "2021-07-05T20:32:40.454Z",
      "updated_date": "2021-07-12T21:44:23.126Z",
      "name": "Springfield Elementary School",
      "grade_levels": [
        "01",
        "02",
        "03",
        "04",
        "05"
      ],
      "locale": "en",
      "time_zone": "America/Chicago",
      "location": {},
      "properties": {},
      "district_id": "00000000-0000-0000-0000-000000000000"
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## Fetch District

### *GET* https://ed.link/api/v2/graph/schools/:school\_id

Retrieve information about a specific **[School](../models/external/school)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `school_id` | `string` | The UUID of the desired **[School](../models/external/school)**. |

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/schools/00000000-0000-0000-0000-000000000000', {
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
    "created_date": "2021-07-05T20:32:40.454Z",
    "updated_date": "2021-07-12T21:44:23.126Z",
    "name": "Springfield Elementary School",
    "grade_levels": [
      "01",
      "02",
      "03",
      "04",
      "05"
    ],
    "locale": "en",
    "time_zone": "America/Chicago",
    "location": {},
    "properties": {},
    "district_id": "00000000-0000-0000-0000-000000000000"
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## List a School's Classes

### *GET* https://ed.link/api/v2/graph/schools/:school\_id/classes

Retrieve a list of **[Classes](../models/external/class)** associated with the
specified **[School](../models/external/school)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `school_id` | `string` | The UUID of the desired **[School](../models/external/school)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/schools/00000000-0000-0000-0000-000000000000/classes', {
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

## List a School's Courses

### *GET* https://ed.link/api/v2/graph/schools/:school\_id/courses

Retrieve a list of **[Courses](../models/external/course)** associated with the
specified **[School](../models/external/school)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `school_id` | `string` | The UUID of the desired **[School](../models/external/school)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/schools/00000000-0000-0000-0000-000000000000/courses', {
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

## List a School's Sessions

### *GET* https://ed.link/api/v2/graph/schools/:school\_id/sessions

Retrieve a list of **[Sessions](../models/external/session)** associated with the
specified **[School](../models/external/school)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `school_id` | `string` | The UUID of the desired **[School](../models/external/school)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/schools/00000000-0000-0000-0000-000000000000/sessions', {
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
      "created_date": "2021-07-13T17:45:27.548Z",
      "updated_date": "2021-07-13T17:45:27.548Z",
      "name": "Fall 2021",
      "start_date": "2021-07-01T00:00:00.000Z",
      "end_date": "2022-01-01T00:00:00.000Z",
      "state": "active",
      "type": "semester",
      "properties": {},
      "school_id": "00000000-0000-0000-0000-000000000000",
      "district_id": "00000000-0000-0000-0000-000000000000"
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## List a School's People

### *GET* https://ed.link/api/v2/graph/schools/:school\_id/people

Retrieve a list of **[People](../models/external/person)** associated with the
specified **[School](../models/external/school)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `school_id` | `string` | The UUID of the desired **[School](../models/external/school)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/schools/00000000-0000-0000-0000-000000000000/people', {
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
      "created_date": "2021-07-13T17:45:39.937Z",
      "updated_date": "2021-07-13T17:45:39.937Z",
      "first_name": "George",
      "middle_name": "Oscar",
      "last_name": "Bluth",
      "display_name": "Gob Bluth",
      "picture_url": "https://static.wikia.nocookie.net/arresteddevelopment/images/7/79/GOB_on_segway.jpg",
      "roles": [
        "administrator"
      ],
      "email": "gob.bluth@example.com",
      "phone": "12345556789",
      "locale": "en",
      "time_zone": "America/Los_Angeles",
      "graduation_year": 1996,
      "grade_levels": [
        "PS"
      ],
      "demographics": {},
      "properties": {},
      "district_id": "00000000-0000-0000-0000-000000000000",
      "school_ids": [
        "00000000-0000-0000-0000-000000000000"
      ]
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## List a School's Administrators

### *GET* https://ed.link/api/v2/graph/schools/:school\_id/administrators

Retrieve a list of **[People](../models/external/person)** with
the [`administrator` role](../models/external/enums/role) associated with the
specified **[School](../models/external/school)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `school_id` | `string` | The UUID of the desired **[School](../models/external/school)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/schools/00000000-0000-0000-0000-000000000000/administrators', {
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
      "created_date": "2021-07-13T17:45:39.937Z",
      "updated_date": "2021-07-13T17:45:39.937Z",
      "first_name": "George",
      "middle_name": "Oscar",
      "last_name": "Bluth",
      "display_name": "Gob Bluth",
      "picture_url": "https://static.wikia.nocookie.net/arresteddevelopment/images/7/79/GOB_on_segway.jpg",
      "roles": [
        "administrator"
      ],
      "email": "gob.bluth@example.com",
      "phone": "12345556789",
      "locale": "en",
      "time_zone": "America/Los_Angeles",
      "graduation_year": 1996,
      "grade_levels": [
        "PS"
      ],
      "demographics": {},
      "properties": {},
      "district_id": "00000000-0000-0000-0000-000000000000",
      "school_ids": [
        "00000000-0000-0000-0000-000000000000"
      ]
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## List a School's Teachers

### *GET* https://ed.link/api/v2/graph/schools/:school\_id/teachers

Retrieve a list of **[People](../models/external/person)** with the [`teacher` role](../models/external/enums/role)
associated with the specified **[School](../models/external/school)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `school_id` | `string` | The UUID of the desired **[School](../models/external/school)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/schools/00000000-0000-0000-0000-000000000000/teachers', {
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
      "grade_levels": [
        "PS"
      ],
      "demographics": {},
      "properties": {},
      "district_id": "00000000-0000-0000-0000-000000000000",
      "school_ids": [
        "00000000-0000-0000-0000-000000000000"
      ]
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## List a School's Students

### *GET* https://ed.link/api/v2/graph/schools/:school\_id/students

Retrieve a list of **[People](../models/external/person)** with the [`student` role](../models/external/enums/role)
associated with the specified **[School](../models/external/school)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `school_id` | `string` | The UUID of the desired **[School](../models/external/school)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/schools/00000000-0000-0000-0000-000000000000/students', {
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
      "grade_levels": [
        "PS"
      ],
      "demographics": {},
      "properties": {},
      "district_id": "00000000-0000-0000-0000-000000000000",
      "school_ids": [
        "00000000-0000-0000-0000-000000000000"
      ]
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```
