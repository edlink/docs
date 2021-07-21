# People

## List All People
### *GET* https://ed.link/api/v1/graph/people

Retrieve a list of all people to whom you have been granted access by this integration. This query allows for [standard paging parameters](/docs/graph/paginated-requests).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v1/graph/people', {
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
        },
        { ... }
    ]
}
```

## Fetch A Person
### *GET* https://ed.link/api/v1/graph/people/:id

Retrieve a single person to whom you have been granted access.

#### Sample Request

```javascript
axios.get('https://ed.link/api/v1/graph/people/3263aea2-52cf-4fc1-8a59-d4641ebfb206', {
    headers: {
        authorization: `Bearer ${integration_access_token}`
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

<!-- ## Create A School
###
`POST https://ed.link/api/v1/graph/people/:person_id`

Retrieve details about a single person.

## Update A Person's Details
###
`PUT https://ed.link/api/v1/graph/people/:person_id`

Change a person's profile details in the source platform.

## Delete A School
###
`DELETE https://ed.link/api/v1/graph/people/:person_id`

Delete a person's account within the source platform. -->