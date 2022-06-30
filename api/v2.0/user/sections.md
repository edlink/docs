# Sections

## List My Sections

### *GET* https://ed.link/api/v2/my/sections

Retrieve a list of all **[Sections](../models/external/section)** in which the current user is enrolled.

#### Request Parameters

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/my/sections', {
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
      "created_date": "2021-07-13T17:45:27.645Z",
      "updated_date": "2021-07-13T17:45:27.645Z",
      "name": "Section 3",
      "description": null,
      "picture_url": null,
      "state": "active",
      "locale": "en",
      "time_zone": "America/Chicago",
      "properties": {},
      "periods": [ "06" ],
      "class_id": "00000000-0000-0000-0000-000000000000"
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## Fetch a Section

### *GET* https://ed.link/api/v2/my/sections/:section\_id

Retrieve information about a specific **[Section](../models/external/section)** in which the current user is enrolled.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `section_id` | `string` | The UUID of the desired **[Section](../models/external/section)**. |

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/my/sections/00000000-0000-0000-0000-000000000000', {
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
    "created_date": "2021-07-13T17:45:27.645Z",
    "updated_date": "2021-07-13T17:45:27.645Z",
    "name": "Section 3",
    "description": null,
    "picture_url": null,
    "state": "active",
    "locale": "en",
    "time_zone": "America/Chicago",
    "properties": {},
    "periods": [ "06" ],
    "class_id": "00000000-0000-0000-0000-000000000000"
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## List a Section's Enrollments

### *GET* https://ed.link/api/v2/my/sections/:section\_id/enrollments

Retrieve a list of **[Enrollments](../models/external/enrollment)** associated with the specified **[Section](../models/external/section)**. The current user must be enrolled in the requested section for this call to succeed.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `section_id` | `string` | The UUID of the desired **[Section](../models/external/section)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/my/sections/00000000-0000-0000-0000-000000000000/enrollments', {
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

## List a Section's People

### *GET* https://ed.link/api/v2/my/sections/:section\_id/people

Retrieve a list of **[People](../models/external/person)** associated with the
specified **[Section](../models/external/section)**. The current user must be enrolled in the requested section for this call to succeed.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `section_id` | `string` | The UUID of the desired **[Section](../models/external/section)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/my/sections/00000000-0000-0000-0000-000000000000/people', {
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

## List a Section's Teachers

### *GET* https://ed.link/api/v2/my/sections/:section\_id/teachers

Retrieve a list of **[People](../models/external/person)** with the [`teacher` role](../models/external/enums/role) associated with the
specified **[Section](../models/external/section)**. The current user must be enrolled in the requested section for this call to succeed.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `section_id` | `string` | The UUID of the desired **[Section](../models/external/section)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/my/sections/00000000-0000-0000-0000-000000000000/teachers', {
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

## List a Section's Students

### *GET* https://ed.link/api/v2/my/sections/:section\_id/students

Retrieve a list of **[People](../models/external/person)** with the [`student` role](../models/external/enums/role) associated with the
specified **[Section](../models/external/section)**. The current user must be enrolled in the requested section for this call to succeed.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `section_id` | `string` | The UUID of the desired **[Section](../models/external/section)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/my/sections/00000000-0000-0000-0000-000000000000/students', {
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
