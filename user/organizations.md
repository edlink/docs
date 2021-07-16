<div class="card notice">
    <p>
        This document details requests that are scoped to a single user.
        A user <a href="/docs/user/authentication">access token</a> is required to make these requests.
        If you are looking for unscoped requests (i.e. requests to retrieve data about all sections, courses, schools),
        please visit the <a href="/docs/graph/organizations">corresponding document</a> under the Graph API section.
    </p>
</div>

These endpoints help you retrieve details about the organization enrollments for users who have logged into your platform with Edlink.
For more details on the data model, visit the [Organizations](/docs/graph/organizations) document on the Graph API. The information retrieved from these
endpoints will be identical to the corresponding organization objects in the Graph API, however, they may be augmented with a `enrollment` field, if
the requesting user is a member of the course, section, or school.

### Organization Types

Any of the following types can be used as an alias for the word `organizations` to filter results. This makes it possible to query for a list of courses, instead of retrieving a list of all organizations and then filtering by `type = 'course'`.

| Organization Type | Typical Parent Type | Description |
|---|---|---|
| `school` | District or None | A school or campus. |
| `department` | School | A department within a school (less common within K-12). |
| `course` | Department or School | A course that is taught at the school. |
| `section` | Course | Groups of students that are taught by the same teacher. |
| `group` | Course | Groups of students created by the teacher for collaboration. |

Typically, you will be using the retrieving items of the `course` and `school` types. Other organization types are less frequently used unless your application has a specific need.

## List Courses, Sections, or Schools
### *GET* https://ed.link/api/v1/my/:organization\_type

This endpoint retrieves a list of organizations in which the user is actively enrolled as a student or teacher. It is similar to the Graph API endpoint,
but is scoped for the requesting user. In addition, it will be enhanced with an `enrollments` field, which contains details about the user's enrollments -
for example, whether they are a student or a teacher in the corresponding organization.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `organization_type` | String | Either `organizations` for all types, or one of the types listed above. |

This request allows for the [standard paging parameters](/docs/graph/paginated-requests).

#### Response Data

This endpoint returns an array of organization objects with added `enrollment` data.

#### Sample Request

``` javascript
axios.get('https://ed.link/api/v1/my/courses', {
    headers: {
        'Authorization': `Bearer ${user_access_token}`
    }
});
```

#### Sample Response

```json
{
    "$data": [
        {
            "id": "497e6606-9e53-41c4-a77a-ad86f678c9b3",
            "type": "course",
            "created_date": "2020-03-08T23:33:11.691Z",
            "updated_date": "2020-03-08T23:33:11.691Z",
            "name": "Algebra 101, Section 1",
            "description": "",
            "icon_url": "https://api.schoology.com/sites/all/themes/schoology_theme/images/course-default.svg",
            "banner_url": "",
            "source_data": {},
            "source": {
                "id": "9aec5b81-fe3c-4629-a989-a75f02d9e947"
            },
            "ancestry": [
                "78ec6e26-2e92-4d6f-a0af-bb6ac7c45986",
                "497e6606-9e53-41c4-a77a-ad86f678c9b3"
            ],
            "terms": [],
            "entity": null,
            "verified": false,
            "enrollments": [
                {
                    "id": "21b4fe22-8830-46ce-ba67-14d412657511",
                    "created_date": "2020-03-08T23:39:18.430Z",
                    "updated_date": "2020-03-08T23:39:18.430Z",
                    "start_date": null,
                    "end_date": null,
                    "type": "teacher",
                    "target": "497e6606-9e53-41c4-a77a-ad86f678c9b3"
                }
            ]
        },
        { ... }
    ]
}
```

## Fetch Details About A Single Organization
### *GET* https://ed.link/api/v1/my/:organization\_type/:course\_id

This endpoint retrieves details about the requested course. The requesting user must be a member of the desired course.
This endpoint is functionally equivalent to the Graph API method, but adds an additional check for user permission.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `organization_type` | String | One of the organization types defined above. |
| `organization_id` | UUID | The UUID corresponding to the organization details you want to retrieve. |

#### Response Data

This endpoint returns a organization object with added person and enrollment fields. If the user is not an active member of the requested course, the request will return a `404` error.

#### Sample Request

``` javascript
axios.get('https://ed.link/api/v1/my/courses/8ab9c040-d458-4746-9bea-99f4b5066f17', {
    headers: {
        'Authorization': `Bearer ${user_access_token}`
    }
});
```

#### Sample Response

```json
{
    "$data": {
        "id": "497e6606-9e53-41c4-a77a-ad86f678c9b3",
        "type": "course",
        "created_date": "2020-03-08T23:33:11.691Z",
        "updated_date": "2020-03-08T23:33:11.691Z",
        "name": "Algebra 101, Section 1",
        "description": "",
        "icon_url": "https://api.schoology.com/sites/all/themes/schoology_theme/images/course-default.svg",
        "banner_url": "",
        "source_data": {},
        "source": {
            "id": "9aec5b81-fe3c-4629-a989-a75f02d9e947"
        },
        "ancestry": [
            "78ec6e26-2e92-4d6f-a0af-bb6ac7c45986",
            "497e6606-9e53-41c4-a77a-ad86f678c9b3"
        ],
        "terms": [],
        "entity": null,
        "verified": false,
        "enrollments": [
            {
                "id": "21b4fe22-8830-46ce-ba67-14d412657511",
                "created_date": "2020-03-08T23:39:18.430Z",
                "updated_date": "2020-03-08T23:39:18.430Z",
                "start_date": null,
                "end_date": null,
                "type": "teacher",
                "target": "497e6606-9e53-41c4-a77a-ad86f678c9b3"
            }
        ]
    }
}
```

## Fetch a List of Users Enrolled in an Organization
### *GET* https://ed.link/api/v1/my/:organization\_type/:organization\_id/enrollments

This endpoint retrieves a list of the members of a specific course. The requesting user must be a member of the desired course.
This endpoint is functionally equivalent to the Graph API method, but adds an additional check for user permission.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `organization_type` | String | One of the organization types defined above. |
| `organization_id` | UUID | The UUID corresponding to the organization details you want to retrieve. |

#### Response Data

This endpoint returns an array of enrollment objects, enriched with the associated user data. If the user is not an active member of the requested course, the request will return a `404` error.

#### Sample Request

``` javascript
axios.get('https://ed.link/api/v1/my/courses/8ab9c040-d458-4746-9bea-99f4b5066f17/enrollments', {
    headers: {
        'Authorization': `Bearer ${user_access_token}`
    }
});
```
