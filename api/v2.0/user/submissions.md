# Submissions

> This page is under construction. User API v2 is in beta and is subject to change.

## List Submissions

### *GET* https://ed.link/api/v2/my/classes/:class\_id/assignments/:assignment\_id/submissions

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
      "state": "created",
      "created_date": "2022-01-27T17:10:09.702Z",
      "attempts": [],
      "id": "00000000-0000-0000-0000-000000000000",
      "person_id": "00000000-0000-0000-0000-000000000000"
    }
  ]
}
```

## Fetch Submission

### *GET* https://ed.link/api/v2/my/classes/:class\_id/assignments/:assignment\_id/submissions/:submission\_id

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
    "state": "created",
    "created_date": "2022-01-27T17:10:09.702Z",
    "attempts": [],
    "id": "00000000-0000-0000-0000-000000000000",
    "person_id": "00000000-0000-0000-0000-000000000000"
  }
}
```

## Update Submission Metadata

### *PATCH* https://ed.link/api/v2/my/classes/:class\_id/assignments/:assignment\_id/submissions/:submission\_id

Update metadata for a specific **[Submission](../models/external/submission)**. This includes submitting grades, comments, or altering due date overrides (setting the due date for an individual student to be different than that of the other assignees.)

The user must be enrolled as a `teacher`, `ta`, `designer`, `administrator`, or `district-administrator` in the class to use this endpoint.

Please review [our guide on patch requests](../../../guides/v2.0/patch-requests) for more information regarding their use.

#### Request Parameters

| Parameter       | Type     | Description                                                              |
|-----------------|----------|--------------------------------------------------------------------------|
| `class_id`      | `string` | The UUID of the desired **[Class](../models/external/class)**.           |
| `assignment_id` | `string` | The UUID of the desired **[Assignment](../models/external/assignment)**. |
| `submission_id` | `string` | The UUID of the desired **[Submission](../models/external/submission)**. |

#### Request Body

The request body should contain a partial **[Submission](../models/external/submission)** object.

The following fields are allowed: `grader_id`, `flags`, `grade_comment`, `grade_points`, `grade`, `extra_attempts`, `override_due_date`.

```json
{
  "grade_points": "12",
  "override_due_date": "2022-01-27T17:10:09.702Z"
}
```

#### Sample Response

The response contains the updated **[Submission](../models/external/submission)** object.

```json
{
  "$request": "00000000-0000-0000-0000-000000000000",
  "$data": {
    "flags": [],
    "state": "submitted",
    "created_date": "2022-01-27T17:10:09.702Z",
    "attempts": [
      {
        "body": {
          "type": "link",
          "url": "https://google.com"
        },
        "created_date": "2022-01-27T17:10:09.702Z"
      }
    ],
    "grade_points": "12",
    "override_due_date": "2022-01-27T17:10:09.702Z",
    "id": "00000000-0000-0000-0000-000000000000",
    "person_id": "00000000-0000-0000-0000-000000000000"
  }
}
```

## Submit Submission

### *POST* https://ed.link/api/v2/my/classes/:class\_id/assignments/:assignment\_id/submit

As a student, submit an attempt for your **[Submission](../models/external/submission)**. This will add it to the `attempts` array seen when retrieving a submission. It will also update the `state` of the submission to `submitted`.

#### Request Parameters

| Parameter       | Type     | Description                                                              |
|-----------------|----------|--------------------------------------------------------------------------|
| `class_id`      | `string` | The UUID of the desired **[Class](../models/external/class)**.           |
| `assignment_id` | `string` | The UUID of the desired **[Assignment](../models/external/assignment)**. |

#### Request Body

The request body should be one of the following formats.

##### Submitting a Link
```json
{
  "type": "link",
  "url": "https://google.com"
}
```

##### Submitting Text
```json
{
  "type": "text",
  "text": "This is the body of a text submission."
}
```

#### Sample Response

The response contains the updated **[Submission](../models/external/submission)** object.

```json
{
  "$request": "00000000-0000-0000-0000-000000000000",
  "$data": {
    "flags": [],
    "state": "submitted",
    "created_date": "2022-01-27T17:10:09.702Z",
    "attempts": [
      {
        "body": {
          "type": "text",
          "url": "This is the body of a text submission."
        },
        "created_date": "2022-01-27T17:10:09.702Z"
      }
    ],
    "override_due_date": "2022-01-29T23:59:59.000Z",
    "id": "00000000-0000-0000-0000-000000000000",
    "person_id": "00000000-0000-0000-0000-000000000000"
  }
}
```

## Reclaim Submission

### *POST* https://ed.link/api/v2/my/classes/:class\_id/assignments/:assignment\_id/reclaim

As a student, reclaim your **[Submission](../models/external/submission)**. This will update the `state` of the submission to `reclaimed`. In order to reclaim the submission, it must be in the `submitted` state.

#### Request Parameters

| Parameter       | Type     | Description                                                              |
|-----------------|----------|--------------------------------------------------------------------------|
| `class_id`      | `string` | The UUID of the desired **[Class](../models/external/class)**.           |
| `assignment_id` | `string` | The UUID of the desired **[Assignment](../models/external/assignment)**. |


#### Sample Request

```javascript
axios.post(`https://ed.link/api/v2/my/classes/${class_id}/assignments/${assignment_id}/reclaim`, {
	headers: {
		authorization: `Bearer ${person_access_token}`
	}
});
```

#### Sample Response

The response contains the updated **[Submission](../models/external/submission)** object.

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
        },
        "created_date": "2022-01-27T17:10:09.702Z"
      },
      {
        "body": {
          "type": "text",
          "url": "This is the body of a text submission."
        },
        "created_date": "2022-01-27T17:10:09.702Z"
      }
    ],
    "override_due_date": "2022-01-29T23:59:59.000Z",
    "id": "00000000-0000-0000-0000-000000000000",
    "person_id": "00000000-0000-0000-0000-000000000000"
  }
}
```

## Return Submission

### *POST* https://ed.link/api/v2/my/classes/:class\_id/assignments/:assignment\_id/submissions/:submission\_id/return

As a teacher, finalize the grade for a **[Submission](../models/external/submission)** and send it back to the assignee.

The user must be enrolled as a `teacher`, `ta`, `designer`, `administrator`, or `district-administrator` in the class to use this endpoint.


#### Request Parameters

| Parameter       | Type     | Description                                                              |
|-----------------|----------|--------------------------------------------------------------------------|
| `class_id`      | `string` | The UUID of the desired **[Class](../models/external/class)**.           |
| `assignment_id` | `string` | The UUID of the desired **[Assignment](../models/external/assignment)**. |
| `submission_id` | `string` | The UUID of the desired **[Submission](../models/external/submission)**. |


#### Sample Request

```javascript
axios.post(`https://ed.link/api/v2/my/classes/${class_id}/assignments/${assignment_id}/submissions/${submission_id}/return`, {
	headers: {
		authorization: `Bearer ${person_access_token}`
	}
});
```

#### Sample Response

The response contains the updated **[Submission](../models/external/submission)** object.

```json
{
  "$request": "00000000-0000-0000-0000-000000000000",
  "$data": {
    "flags": [],
    "state": "returned",
    "created_date": "2022-01-27T17:10:09.702Z",
    "attempts": [
      {
        "body": {
          "type": "link",
          "url": "https://google.com"
        },
        "created_date": "2022-01-27T17:10:09.702Z"
      },
      {
        "body": {
          "type": "text",
          "url": "This is the body of a text submission."
        },
        "created_date": "2022-01-27T17:10:09.702Z"
      }
    ],
    "grade_points": "12",
    "override_due_date": "2022-01-29T23:59:59.000Z",
    "id": "00000000-0000-0000-0000-000000000000",
    "person_id": "00000000-0000-0000-0000-000000000000"
  }
}
```
