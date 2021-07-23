# Schools

## List Schools

### *GET* https://ed.link/api/v2/graph/schools

Retrieve a list of all **[Schools](../models/external/school)**. There should always be exactly one district.

#### Request Parameters

This query allows for [standard paging parameters](paginated-requests).

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
