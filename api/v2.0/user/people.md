# People

These endpoints help you retrieve details about users who have logged into your platform with Edlink. The information retrieved from these endpoints will be identical
to the corresponding user objects in the Graph API. This makes it very simple to match up a user after their login with a pre-imported user.

## Fetch Your Own Profile Data
### *GET* https://ed.link/api/v1/my/profile

This endpoint retrieves the personal information of the user that corresponds to the provided bearer token. There are no special permissions
required to access this endpoint, as a user can always retrieve their own details. This endpoint returns a [standard user object](/docs/api/v2.0/models/person).

#### Sample Request

``` javascript
const user = await axios.get('https://ed.link/api/v2/my/profile', {
    headers: {
        'Authorization': `Bearer ${user_access_token}`
    }
});
```

#### Sample Response

```json
{
    "$request": "00000000-0000-0000-0000-000000000000",
    "$data": {
        "id": "00000000-0000-0000-0000-000000000000",
        "created_date": "2021-08-09T23:06:57.290Z",
        "updated_date": "2021-10-22T04:43:30.338Z",
        "first_name": "Bart",
        "middle_name": "",
        "last_name": "Simpson",
        "display_name": "Bart Simpson",
        "roles": [
            "student"
        ],
        "graduation_year": "2000",
        "grade_levels": [ "04" ],
        "picture_url": null,
        "email": "bsimpson@springfieldelementary.edu",
        "phone": "555-555-5555",
        "locale": "en",
        "time_zone": "America/Los_Angeles",
        "demographics": {
            "birthday": 1982-02-23T00:00:00.000Z,
            "gender": "male",
            "residence_status": "01652",
            "english_language_learner": false,
            "country_of_birth": "USA",
            "state_of_birth": "OR",
            "city_of_birth": "Springfield",
            "hispanic_or_latino_ethnicity": false,
            "races": []
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