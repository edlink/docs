# Districts

## List Districts

### *GET* https://ed.link/api/v2/graph/districts

Retrieve a list of all **[Districts](district)**. There should always be exactly one district.

#### Request Parameters

This query allows for [standard paging parameters](/docs/graph/paginated-requests).

#### Sample Request

```typescript
// List all districts.
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
