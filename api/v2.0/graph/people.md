# People

## List People

### *GET* https://ed.link/api/v2/graph/people

Retrieve a list of all **[People](../models/external/person)**.

#### Request Parameters

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/people', {
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

## Fetch Person

### *GET* https://ed.link/api/v2/graph/people/:person\_id

Retrieve information about a specific **[Person](../models/external/person)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `person_id` | `string` | The UUID of the desired **[Person](../models/external/person)**. |

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/people/00000000-0000-0000-0000-000000000000', {
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
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## List a Person's Enrollments

### *GET* https://ed.link/api/v2/graph/people/:person\_id/enrollments

Retrieve a list of **[Enrollments](../models/external/enrollment)** associated with the
specified **[Person](../models/external/person)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `person_id` | `string` | The UUID of the desired **[Person](../models/external/person)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/people/00000000-0000-0000-0000-000000000000/enrollments', {
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

## List a Person's Districts

### *GET* https://ed.link/api/v2/graph/people/:person\_id/districts

Retrieve a list of **[Districts](../models/external/district)** associated with the
specified **[Person](../models/external/person)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `person_id` | `string` | The UUID of the desired **[Person](../models/external/person)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/people/00000000-0000-0000-0000-000000000000/districts', {
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
      "name": "Gravity Falls School District",
      "locale": "en",
      "time_zone": "America/Los_Angeles",
      "location": {},
      "properties": {}
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## List a Person's Schools

### *GET* https://ed.link/api/v2/graph/people/:person\_id/schools

Retrieve a list of **[Schools](../models/external/school)** associated with the
specified **[Person](../models/external/person)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `person_id` | `string` | The UUID of the desired **[Person](../models/external/person)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/people/00000000-0000-0000-0000-000000000000/schools', {
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

## List a Person's Classes

### *GET* https://ed.link/api/v2/graph/people/:person\_id/classes

Retrieve a list of **[Classes](../models/external/class)** associated with the
specified **[Person](../models/external/person)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `person_id` | `string` | The UUID of the desired **[Person](../models/external/person)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/people/00000000-0000-0000-0000-000000000000/classes', {
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

## List a Person's Sections

### *GET* https://ed.link/api/v2/graph/people/:person\_id/sections

Retrieve a list of **[Sections](../models/external/section)** associated with the
specified **[Person](../models/external/person)**.

#### Request Parameters

| Parameter   | Type     | Description                                                      |
|-------------|----------|------------------------------------------------------------------|
| `person_id` | `string` | The UUID of the desired **[Person](../models/external/person)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/people/00000000-0000-0000-0000-000000000000/sections', {
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

## List a Person's Agents

### *GET* https://ed.link/api/v2/graph/people/:person\_id/agents

Retrieve a list of **[Agents](../models/external/agent)** that reference the
specified **[Person](../models/external/person)** in either the `observer_id` or `target_id` field.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `person_id` | `string` | The UUID of the desired **[Person](../models/external/person)**. |

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/people/00000000-0000-0000-0000-000000000000/agents', {
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
      "relationship": "parent",
      "properties": {},
      "observer_id": "00000000-0000-0000-0000-000000000000",
      "target_id": "00000000-0000-0000-0000-000000000000"
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

