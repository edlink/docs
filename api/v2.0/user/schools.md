# Schools

> User API v2 is in beta and is subject to change.

## List Schools

### *GET* https://ed.link/api/v2/my/schools

Retrieve a list of **[Schools](../models/external/school)** that the current user is associated with. A person may be associated with any number of schools, including zero (e.g. if they're a district administrator, or their LMS was set up incorrectly). Some systems that Edlink connects to do not natively support the concept of schools. In these cases, Edlink will create a default **[School](../models/external/school)** object that will contain all of the classes.

#### Request Parameters

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/my/schools', {
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
      "name": "Sample School",
      "created_date": "2021-07-13T17:45:27.218Z",
      "updated_date": "2022-01-26T22:44:36.078Z",
      "locale": null,
      "location": {},
      "time_zone": null,
      "grade_levels": [],
      "properties": {},
      "identifiers": [],
      "district_id": "00000000-0000-0000-0000-000000000000"
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## Fetch A Single School

### *GET* https://ed.link/api/v2/my/schools/:school_id

Retrieve information about the specific **[School](../models/external/school)** that the current user is associated with.

#### Request Parameters

| Parameter  | Type     | Description                                                    |
|------------|----------|----------------------------------------------------------------|
| `school_id` | `string` | The UUID of the desired **[School](../models/external/school)**. |

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/my/schools/00000000-0000-0000-0000-000000000000', {
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
    "name": "Sample School",
    "created_date": "2021-07-13T17:45:27.218Z",
    "updated_date": "2022-01-26T22:44:36.078Z",
    "locale": null,
    "location": {},
    "time_zone": null,
    "grade_levels": [],
    "properties": {},
    "identifiers": [],
    "district_id": "00000000-0000-0000-0000-000000000000"
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```