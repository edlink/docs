# Enrollments

## List All Available Enrollments
### *GET* https://ed.link/api/v1/graph/enrollments

Retrieve a list of all enrollments to which you have been granted access. This query allows for [standard paging parameters](/docs/graph/paginated-requests).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v1/graph/enrollments', {
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
            "id": "26b4acdb-0be2-49d6-b51e-22f6957481ff",
            "created_date": "2020-02-11T03:01:16.284Z",
            "updated_date": "2020-02-11T03:01:16.284Z",
            "start_date": null,
            "end_date": null,
            "type": "teacher",
            "person": {
                "id": "a8e1a134-834a-4113-9418-66857a50bfce",
                "created_date": "2019-11-19T17:13:43.655Z",
                "updated_date": "2019-11-19T17:13:43.655Z",
                "first_name": "John",
                "middle_name": "",
                "last_name": "Doe",
                "display_name": "John Doe",
                "picture_url": "",
                "email": ""
            },
            "organization": {
                "id": "9e51aa36-3755-4d70-bb9c-075f1a35b7be"
            }
        },
        { ... }
    ]
}
```

## Fetch A Single Enrollment
### *GET* https://ed.link/api/v1/graph/enrollments/:enrollment\_id

Retrieve a single enrollment.

#### Sample Request

```javascript
axios.get('https://ed.link/api/v1/graph/enrollments/3263aea2-52cf-4fc1-8a59-d4641ebfb206', {
    headers: {
        authorization: `Bearer ${integration_access_token}`
    }
});
```

#### Sample Response

```json
{
    "$data": {
        "id": "26b4acdb-0be2-49d6-b51e-22f6957481ff",
        "created_date": "2020-02-11T03:01:16.284Z",
        "updated_date": "2020-02-11T03:01:16.284Z",
        "start_date": null,
        "end_date": null,
        "type": "teacher",
        "person": {
            "id": "a8e1a134-834a-4113-9418-66857a50bfce",
            "created_date": "2019-11-19T17:13:43.655Z",
            "updated_date": "2019-11-19T17:13:43.655Z",
            "first_name": "John",
            "middle_name": "",
            "last_name": "Doe",
            "display_name": "John Doe",
            "picture_url": "",
            "email": ""
        },
        "organization": {
            "id": "9e51aa36-3755-4d70-bb9c-075f1a35b7be"
        }
    }
}
```

<!-- ### Create A Enrollment
#### Retrieve a single school to which you have been granted access.
`POST https://ed.link/api/v1/graph/enrollments/:enrollment_id`

Information

### Update A Enrollment
#### Update a single student or teacher enrollment.
`PUT https://ed.link/api/v1/graph/enrollments/:enrollment_id`

Information

### Delete A Enrollment
#### Remove a person from the course in which they are enrolled.
`DELETE https://ed.link/api/v1/graph/enrollments/:enrollment_id`

Information -->