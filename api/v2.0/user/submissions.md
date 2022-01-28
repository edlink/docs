# Submissions

> This page is under construction. User API v2 is in beta and is subject to change.

## List Submissions

### *GET* https://ed.link/api/v2/my/classes/:class_id/assignments/:assignment_id/submissions

Retrieve a list of **[Submissions](../models/external/submission)** for a given **[Assignment](../models/external/assignment)**.

If the user is enrolled as a `teacher`, `ta`, `designer`, `administrator`, or `district-administrator` in the class, this will return all submissions. If not, this will return only the user's own submission.

#### Request Parameters

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

| Parameter       | Type     | Description                                                              |
|-----------------|----------|--------------------------------------------------------------------------|
| `class_id`      | `string` | The UUID of the desired **[Class](../models/external/class)**.           |
| `assignment_id` | `string` | The UUID of the desired **[Assignment](../models/external/assignment)**. |

#### Sample Request

```javascript
axios.get(`https://ed.link/api/v2/my/classes/${class_id}/assignments/${assignment_id}/submissions`, {
	headers: {
		authorization: `Bearer ${person_access_token}`
	}
});
```

#### Sample Response

```json
{
  "$request": "00000000-0000-0000-0000-000000000000",
  "$data": [
    {
      "flags": [],
      "state": "reclaimed",
      "created_date": "2022-01-27T17:10:09.702Z",
      "attempts": [
        {
          "body": {
            "type": "link",
            "url": "https://google.com"
          }
        }
      ],
      "id": "00000000-0000-0000-0000-000000000000",
      "person_id": "00000000-0000-0000-0000-000000000000"
    }
  ]
}
```

## Fetch Submission

### *GET* https://ed.link/api/v2/my/classes/:class_id/assignments/:assignment_id/submissions/:submission_id

Retrieve information about a specific **[Submission](../models/external/submission)**.

#### Request Parameters

| Parameter       | Type     | Description                                                              |
|-----------------|----------|--------------------------------------------------------------------------|
| `class_id`      | `string` | The UUID of the desired **[Class](../models/external/class)**.           |
| `assignment_id` | `string` | The UUID of the desired **[Assignment](../models/external/assignment)**. |
| `submission_id` | `string` | The UUID of the desired **[Submission](../models/external/submission)**. |

#### Sample Request

```javascript
axios.get(`https://ed.link/api/v2/my/classes/${class_id}/assignments/${assignment_id}`, {
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
    "flags": [],
    "state": "reclaimed",
    "created_date": "2022-01-27T17:10:09.702Z",
    "attempts": [
      {
        "body": {
          "type": "link",
          "url": "https://google.com"
        }
      }
    ],
    "id": "00000000-0000-0000-0000-000000000000",
    "person_id": "00000000-0000-0000-0000-000000000000"
  }
}
```
