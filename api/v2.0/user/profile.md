# My Profile

> This page is under construction. User API v2 is in beta and is subject to change.

## Fetch My Profile

### *GET* https://ed.link/api/v2/my/profile

Retrieve the current **[Person](../models/external/person)**.

#### Sample Request

```javascript
axios.get(`https://ed.link/api/v2/my/profile`, {
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
    "id": "00000000-0000-0000-0000-000000000000",
    "created_date": "2021-07-15T04:05:34.732Z",
    "updated_date": "2022-01-26T22:44:36.089Z",
    "first_name": "Mabel",
    "middle_name": null,
    "last_name": "Pines",
    "display_name": "Mabel Pines",
    "roles": [
      "student"
    ],
    "graduation_year": null,
    "grade_levels": null,
    "picture_url": null,
    "email": "whatever@ed.link",
    "phone": "425-555-5555",
    "locale": "en",
    "time_zone": "America/Los_Angeles",
    "demographics": {
      "birthday": null,
      "gender": "female",
      "residence_status": null,
      "english_language_learner": false,
      "country_of_birth": "USA",
      "state_of_birth": "OR",
      "city_of_birth": "Gravity Falls",
      "hispanic_or_latino_ethnicity": null,
      "races": null
    },
    "properties": {},
    "identifiers": [],
    "district_id": "00000000-0000-0000-0000-000000000000",
    "school_ids": [
      "00000000-0000-0000-0000-000000000000"
    ]
  }
}
```
