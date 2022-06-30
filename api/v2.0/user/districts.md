# Districts

## List Districts

### *GET* https://ed.link/api/v2/my/districts

Retrieve a list of **[Districts](../models/external/district)** that the current user is associated with. There is always one and only one district for a given user. This endpoint exists for API consistency. This endpoint *does* support standard paging a filtering query parameters, but they are almost certainly not needed.

#### Request Parameters

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

This query allows for [filtering results](../../../guides/v2.0/filtering-results).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/my/districts', {
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
      "created_date": "2021-07-13T17:45:27.205Z",
      "updated_date": "2022-01-26T22:44:36.067Z",
      "name": "Sample District",
      "locale": null,
      "location": {},
      "time_zone": null,
      "properties": {},
      "identifiers": []
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## Fetch A Single District

### *GET* https://ed.link/api/v2/my/districts/:district_id

Retrieve information about the specific **[District](../models/external/district)** that the current user is associated with.

#### Request Parameters

| Parameter  | Type     | Description                                                    |
|------------|----------|----------------------------------------------------------------|
| `district_id` | `string` | The UUID of the desired **[District](../models/external/district)**. |

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/my/districts/00000000-0000-0000-0000-000000000000', {
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
    "created_date": "2021-07-13T17:45:27.205Z",
    "updated_date": "2022-01-26T22:44:36.067Z",
    "name": "Sample District",
    "locale": null,
    "location": {},
    "time_zone": null,
    "properties": {},
    "identifiers": []
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```