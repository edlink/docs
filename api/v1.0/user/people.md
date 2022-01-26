# People

These endpoints help you retrieve details about users who have logged into your platform with Edlink. For more details on the data model,
visit the [People](/docs/graph/people) document on the Graph API. The information retrieved from these endpoints will be identical
to the corresponding user objects in the Graph API. This makes it very simple to match up a user after their login with a pre-imported user.

## Fetch Your Own Profile Data
### *GET* https://ed.link/api/v1/my/profile

This endpoint retrieves the personal information of the user that corresponds to the provided bearer token. There are no special permissions
required to access this endpoint, as a user can always retrieve their own details. This endpoint returns a [standard user object](/docs/api/v1.0/models/person).
<!-- This endpoint is a convenience method for developers, and is
functionally equivalent to the method below (if called with the user's own ID). -->

#### Sample Request

``` javascript
const user = await axios.get('https://ed.link/api/v1/my/profile', {
    headers: {
        'Authorization': `Bearer ${user_access_token}`
    }
});
```

#### Sample Response

```json
{
    "$data": {
        "id": "af40a896-5f96-41ca-8031-84cdf72e3559",
        "created_date": "2019-11-19T17:13:43.655Z",
        "updated_date": "2020-02-11T02:57:11.106Z",
        "first_name": "John",
        "middle_name": "",
        "last_name": "Doe",
        "display_name": "John Doe",
        "picture_url": "",
        "birthday": null,
        "gender": null,
        "email": "jdoe@ed.link",
        "phone": "",
        "locale": "",
        "time_zone": ""
    }
}
```

<!-- ## Fetch A User's Profile Data

`GET https://ed.link/api/v1/graph/people/:person_id`

This endpoint retrieves the personal information of the user that corresponds to the provided ID.
This endpoint is very similar to the equivalent within the Graph API. The key difference is that Edlink checks the permissions of the calling user
to make sure that they are allowed to retrieve the details of the specified ID. This is so we can remain in compliance with legal standards (e.g. FERPA) and
common-sense best practices.

For example, students cannot retrieve data about other students, and teachers cannot retrieve data about students who are not enrolled in their courses.

#### Request Parameters

| Parameter | Description |
|---|---|
| `person_id` | The Edlink UUID corresponding to the person whose details you want to retrieve. |

#### Response Data

This endpoint returns a standard user object.

#### Sample Request

``` javascript
const user = await axios.get('https://ed.link/api/v1/graph/people/8ab9c040-d458-4746-9bea-99f4b5066f17');
``` -->