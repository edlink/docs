Organizations are a base class in the Edlink Graph API. Organizations may contain people (through [enrollments](/docs/graph/enrollments)) or they may contain other organizations. In the Graph API, you may access organizations directly, or through a set of aliases that we provide for convenience.

One of the challenges of modeling organizational units in any abstract system is that data sources can vary wildly in their implementations.

### The Organization Object

| Property | Type | Description |
|---|---|---|
| `id` | UUID | A stable UUID representing this integration. |
| `type` | String | The type of this organization (e.g. a course). See the available types below. |
| `name` | String | The display name of this organization. |
| `description` | String | A short description for this organization. |
| `icon_url` | String | A URL to an icon or profile picture for this organization. |
| `state` | String | The state in which the organization is located. |
| `time_zone` | String | The time zone in which the organization is located. |
| `ancestry` | Array | An array of organization UUIDs representing the parents of this organization. |
| `terms` | Array | An array of term UUIDs to which the course belongs. |
| `entity` | Entity | Metadata about the physical entity (e.g. a school building). |
| `source` | Source | Metadata about the source to which this organization belongs. |

### Organization Types

Any of the following types can be used as an alias for the word `organization` to filter results. This makes it possible to query for a list of courses, instead of retrieving a list of all organizations and then filtering by `type = 'course'`.

| Organization Type | Typical Parent Type | Description |
|---|---|---|
| `district` | None (Integration Root) | A collection of schools. |
| `school` | District or None | A school or campus. |
| `department` | School | A department within a school (less common within K-12). |
| `course` | Department or School | A course that is taught at the school. |
| `section` | Course | Groups of students that are taught by the same teacher. |
| `group` | Course | Groups of students created by the teacher for collaboration. |

#### Additional Notes

* Sections are much more common at the post-secondary level (e.g. colleges and universities). They typically represent something like a Monday/Wednesday/Friday or Tuesday/Thursday section, where the professor may be the same, but schedules, teaching assistants, and coursework may vary.
* Groups may vary slightly by platform, but are generally created by teachers manually within their LMS to have students work on projects or collaborate outside of the typical course context.
* Edlink does not currently have an organization type that represents a "catalog course" or "course template" (something that is modeled by the "course" object in OneRoster, for example).
* Not all fields will be available for all organizations. For example, while a school may have a street address, a course (more than likely) will not.

## List Organizations
### *GET* https://ed.link/api/v1/graph/:organization\_type

Retrieve a list all available organizations of the desired type. If you want to retrieve all organizations at once of all types (i.e. all schools, courses, sections), you can use the type `organizations`.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `organization_type` | String | Either `organizations` for all types, or one of the types listed above. |

This query allows for [standard paging parameters](/docs/graph/paginated-requests).

#### Sample Request

```javascript
//List all organizations of any type with the `organizations` alias.
axios.get('https://ed.link/api/v1/graph/organizations', {
    headers: {
        authorization: `Bearer ${integration_access_token}`
    }
});

//You can use use the URL parameter to fetch only courses (for example).
axios.get('https://ed.link/api/v1/graph/courses', {
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
            "id": "38829c39-b204-4b14-8bb7-3e083199d6fc",
            "type": "course",
            "created_date": "2020-02-11T02:57:11.052Z",
            "updated_date": "2020-02-11T02:57:11.052Z",
            "name": "Sample Course",
            "description": "",
            "ancestry": [
                "341efa81-45b9-4c5d-9f8d-59e7fd5475dd",
                "38829c39-b204-4b14-8bb7-3e083199d6fc"
            ],
            "website": "",
            "icon_url": "",
            "state": "active",
            "time_zone": "America/Chicago",
            "terms": [],
            "source": {
                "id": "13b7a412-b692-4836-9513-62e7a5894ee5"
            }
        },
        { ... }
    ]
}
```

## Fetch A Single Organization
### *GET* https://ed.link/api/v1/graph/:organization\_type/:organization\_id

Retrieve information about a specific course.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `organization_type` | String | Either `organizations` for all types, or one of the types listed above. |
| `organization_id` | UUID | The UUID of the desired organization. |


#### Sample Request

```javascript
axios.get('https://ed.link/api/v1/graph/organizations/77a69705-41a7-49cb-0fe8-ffd425f9716f', {
    headers: {
        authorization: `Bearer ${integration_access_token}`
    }
});
```

#### Sample Response

```json
{
    "$data": {
        "id": "38829c39-b204-4b14-8bb7-3e083199d6fc",
        "type": "course",
        "created_date": "2020-02-11T02:57:11.052Z",
        "updated_date": "2020-02-11T02:57:11.052Z",
        "name": "Sample Course",
        "description": "",
        "ancestry": [
            "341efa81-45b9-4c5d-9f8d-59e7fd5475dd",
            "38829c39-b204-4b14-8bb7-3e083199d6fc"
        ],
        "state": "active",
        "time_zone": "America/Chicago",
        "terms": [],
        "source": {
            "id": "13b7a412-b692-4836-9513-62e7a5894ee5"
        }
    }
}
```

## Create an Organization
### *POST* https://ed.link/api/v1/graph/:organization\_type

Creates a new organization in the source system. The new organization will be returned as a result of this call. When a new organization is created in this way, events are also created and webhooks are fired. If the `organization_type` of `organizations` is specified in the URL parameter, then Edlink will look for a JSON body parameter instead to determine what type of organization you're looking to create. If both are specified (URL parameter and JSON body parameter), the JSON body parameter will take precedence.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `organization_type` | String | Either `organizations`, or one of the types listed above. |

#### Request Body

This request expects a JSON body containing the following parameters.

```javascript
{
    "organization_type": "course",
    ""
}
```


#### Sample Request

```javascript
axios.get('https://ed.link/api/v1/graph/organizations', {
    headers: {
        authorization: `Bearer ${integration_access_token}`
    }
});
```

#### Sample Response

```json
{
    "$data": {
        "id": "38829c39-b204-4b14-8bb7-3e083199d6fc",
        "type": "course",
        "created_date": "2020-02-11T02:57:11.052Z",
        "updated_date": "2020-02-11T02:57:11.052Z",
        "name": "Sample Course",
        "description": "",
        "ancestry": [
            "341efa81-45b9-4c5d-9f8d-59e7fd5475dd",
            "38829c39-b204-4b14-8bb7-3e083199d6fc"
        ],
        "state": "active",
        "time_zone": "America/Chicago",
        "terms": [],
        "source": {
            "id": "13b7a412-b692-4836-9513-62e7a5894ee5"
        }
    }
}
```

## List Enrollments by Organization
### *GET* https://ed.link/api/v1/graph/:organization\_type/:organization\_id/:enrollment_type

Retrieve a list of people who are enrolled in the desired organization. Additionally, you can filter by `enrollment_type`, which may be set to one of: `enrollments`, `students`, `teachers`, etc.

This call is recursive, which means that it will return *all enrollments* from *all organizations* that are children of the selected organization. As a practical example: if you are listing the students in a college math course (with M/W/F and T/Th sections), it will return all enrollments from both sections. There is an important case to consider here: while a user can only ever have one enrollment per organization, users may have enrollments at a child organization.

If you're not sure of the organization type, you can use `organizations` and the request will work as expected. However, if you use the incorrect organization type, it will return a `404` error.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `organization_type` | String | Either `organizations` for all types, or one of the types listed above. |
| `organization_id` | UUID | The UUID of the desired organization. |
| `enrollment_type` | String | Either `enrollments` for all types, or one of the [enrollment types](/docs/graph/enrollments). |

This query allows for [standard paging parameters](/docs/graph/paginated-requests).

#### Sample Request

```javascript
//This request will retrieve a list of all enrollments within an organization (e.g. a course).
axios.get('https://ed.link/api/v1/graph/organizations/77a69705-41a7-49cb-0fe8-ffd425f9716f/enrollments', {
    headers: {
        authorization: `Bearer ${integration_access_token}`
    }
});

//This request will retrieve a list of all students enrolled in an organization (e.g. a course).
//Note that last parameter in the URL can be modified to retrieve the desired enrollment type.
axios.get('https://ed.link/api/v1/graph/organizations/77a69705-41a7-49cb-0fe8-ffd425f9716f/students', {
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
            "id": "5466397b-d702-4066-8d6a-6042ed115512",
            "created_date": "2020-02-11T03:01:16.284Z",
            "updated_date": "2020-02-11T03:01:16.284Z",
            "start_date": null,
            "end_date": null,
            "type": "teacher",
            "person": {
                "id": "8ce22870-f8a6-4caf-8ffa-023dda5f7d2e",
                "created_date": "2019-11-19T17:13:43.655Z",
                "updated_date": "2019-11-19T17:13:43.655Z",
                "first_name": "John",
                "middle_name": "",
                "last_name": "Doe",
                "display_name": "John Doe",
                "picture_url": "",
                "birthday": null,
                "gender": null,
                "email": "",
                "phone": "",
                "locale": "",
                "time_zone": ""
            },
            "organization": {
                "id": "38829c39-b204-4b14-8bb7-3e083199d6fc"
            }
        },
        { ... }
    ]
}
```