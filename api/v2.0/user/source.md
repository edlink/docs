# Source

## Fetch My Source

### *GET* https://ed.link/api/v2/my/source

Retrieve the **[Source](../models/internal/source)** that the current user belongs to.

#### Sample Request

```javascript
axios.get(`https://ed.link/api/v2/my/source`, {
	headers: {
		authorization: `Bearer ${person_access_token}`
	}
});
```

#### Sample Response

```json
{
  "$request": "00000000-0000-0000-0000-000000000000",
  "$data": {
    "state": "active",
    "id": "00000000-0000-0000-0000-000000000000",
    "created_date": "2020-02-14T17:20:06.254Z",
    "updated_date": "2020-02-14T17:20:06.254Z",
    "name": "Springfield School District Canvas",
    "sync_interval": 86400,
    "provider_id": "00000000-0000-0000-0000-000000000000",
    "properties": {},
    "team_id": "00000000-0000-0000-0000-000000000000",
    "provider": {
      "active": true,
      "requires_administrator_login": true,
      "requires_administrator_consent": false,
      "requires_remote_configuration": false,
      "allows_data_sync": true,
      "id": "00000000-0000-0000-0000-000000000000",
      "name": "Canvas",
      "application": "canvas"
    }
  }
}
```
