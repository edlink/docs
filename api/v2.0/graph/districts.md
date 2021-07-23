# Districts

## List Districts

### *GET* https://ed.link/api/v2/graph/districts

Retrieve a list of all **[Districts](../models/external/district)**. There should always be exactly one district.

#### Request Parameters

This query allows for [standard paging parameters](paginated-requests).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/districts', {
	headers: {
		authorization: `Bearer ${integration_access_token}`
	}
});
```

#### Sample Response

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

## Fetch District

### *GET* https://ed.link/api/v2/graph/districts/:district\_id

Retrieve information about a specific **[District](../models/external/district)**.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `district_id` | `string` | The UUID of the desired **[District](../models/external/district)**. |

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/districts/00000000-0000-0000-0000-000000000000', {
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
    "name": "Gravity Falls School District",
    "locale": "en",
    "time_zone": "America/Los_Angeles",
    "location": {},
    "properties": {}
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## List District Administrators

### *GET* https://ed.link/api/v2/graph/districts/:district\_id/administrators

Retrieve a list of all **[People](../models/external/person)** with the [district-administrator role](../models/external/enums/role) in the specified **[District](../models/external/district)**.

#### Sample Request

```javascript
axios.get('https://ed.link/api/v2/graph/districts/00000000-0000-0000-0000-000000000000/administrators', {
	headers: {
		authorization: `Bearer ${integration_access_token}`
	}
});
```
