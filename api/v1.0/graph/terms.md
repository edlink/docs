Terms are Edlink's representation of academic sessions. In essence, they are time periods to which organizations can be attached. Schools may use terms to indicate quarters, semesters, or some other timeframe by which they track their students' performance. In Edlink, any organization (e.g. a course) may be tied to one or more terms. For example, a single course may span all four quarters of the academic year. Each quarter may represent a distinct grading or reporting period. Some organizations may also have just one term, or none at all. Terms are particularly relevant if your application produces graded items that it must report back to the LMS or SIS.

### The Term Object
| Property | Type | Description |
|---|---|---|
| `id` | UUID | A stable UUID representing this term. |
| `name` | String | The display name of this term. |
| `start_date` | Date | The ISO-8601 date when the term begins. |
| `end_date` | Date | The ISO-8601 date when the term ends. |

## List All Terms
### *GET* https://ed.link/api/v1/graph/terms

Retrieve a list of all terms. This query allows for [standard paging parameters](/docs/graph/paginated-requests).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v1/graph/terms', {
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
            "id": "3263aea2-52cf-4fc1-8a59-d4641ebfb206",
            "name": "Default Term",
            "created_date": "2019-11-19T17:13:43.661Z",
            "updated_date": "2019-11-19T17:13:43.661Z",
            "start_date": null,
            "end_date": null,
            "source": {
                "id": "13b7a412-b692-4836-9513-62e7a5894ee5"
            }
        },
        { ... }
    ]
}
```

## Fetch A Term
### *GET* https://ed.link/api/v1/graph/terms/:id

Retrieve information about a specific term. No additional data will be provided by this endpoint that is not also provided in the endpoint above. It is simply offered for convenience.

#### Sample Request

```javascript
axios.get('https://ed.link/api/v1/graph/terms/3263aea2-52cf-4fc1-8a59-d4641ebfb206', {
    headers: {
        authorization: `Bearer ${integration_access_token}`
    }
});
```

#### Sample Response

```json
{
    "$data": {
        "id": "3263aea2-52cf-4fc1-8a59-d4641ebfb206",
        "name": "Default Term",
        "created_date": "2019-11-19T17:13:43.661Z",
        "updated_date": "2019-11-19T17:13:43.661Z",
        "start_date": null,
        "end_date": null,
        "source": {
            "id": "13b7a412-b692-4836-9513-62e7a5894ee5"
        }
    }
}
```