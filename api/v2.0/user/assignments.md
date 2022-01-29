# Assignments

> This page is under construction. User API v2 is in beta and is subject to change.

## List Assignments

### *GET* https://ed.link/api/v2/my/classes/:class_id/assignments

Retrieve a list of **[Assignments](../models/external/assignment)** for a given class.

#### Request Parameters

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

| Parameter  | Type     | Description                                                    |
|------------|----------|----------------------------------------------------------------|
| `class_id` | `string` | The UUID of the desired **[Class](../models/external/class)**. |

#### Sample Request

```javascript
axios.get(`https://ed.link/api/v2/my/classes/${class_id}/assignments`, {
	headers: {
		authorization: `Bearer ${person_access_token}`
	}
});
```

#### Sample Response

```json
{
  "$data": [
    {
      "attachments": [],
      "assignee_mode": "all",
      "grading_type": "points",
      "max_attempts": 1,
      "title": "Week 12 Homework",
      "submission_types": [
        "link"
      ],
      "state": "open",
      "created_date": "2021-12-23T22:24:39.934Z",
      "updated_date": "2022-01-03T20:49:09.233Z",
      "due_date": "2022-01-28T18:00:24.573Z",
      "id": "00000000-0000-0000-0000-000000000000",
      "category_id": "00000000-0000-0000-0000-000000000000"
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## Fetch Assignment

### *GET* https://ed.link/api/v2/my/classes/:class_id/assignments/:assignment_id

Retrieve information about a specific **[Assignment](../models/external/assignment)**.

#### Request Parameters 

| Parameter       | Type     | Description                                                              |
|-----------------|----------|--------------------------------------------------------------------------|
| `class_id`      | `string` | The UUID of the desired **[Class](../models/external/class)**.           |
| `assignment_id` | `string` | The UUID of the desired **[Assignment](../models/external/assignment)**. |

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
  "$data": {
    "attachments": [],
    "assignee_mode": "all",
    "grading_type": "points",
    "max_attempts": 1,
    "title": "Week 12 Homework",
    "submission_types": [
      "link"
    ],
    "state": "open",
    "points_possible": 10,
    "created_date": "2021-12-23T22:24:39.934Z",
    "updated_date": "2022-01-03T20:49:09.233Z",
    "due_date": "2022-01-28T18:00:24.573Z",
    "id": "00000000-0000-0000-0000-000000000000",
    "category_id": "00000000-0000-0000-0000-000000000000"
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## Create Assignment

### *POST* https://ed.link/api/v2/my/classes/:class_id/assignments

Create a new assignment in the given **[Class](../models/external/class)**.

The user must be enrolled as a `teacher`, `ta`, `designer`, `administrator`, or `district-administrator` in the class to use this endpoint.

#### Request Parameters

| Parameter  | Type     | Description                                                    |
|------------|----------|----------------------------------------------------------------|
| `class_id` | `string` | The UUID of the desired **[Class](../models/external/class)**. |

#### Request Body

The request body should contain an **[Assignment](../models/external/assignment)** object.

The following fields are allowed: `title`, `description`, `description_plaintext`, `attachments`, `due_date`, `display_date`, `start_date`, `end_date`, `assignee_mode`, `assignee_ids`, `points_possible`, `grading_type`, `submission_types`, `max_attempts`, `session_id`, `category_id`.

The following fields are required: `title`, `description`, `due_date`, `grading_type`.

```json
{
  "title": "Week 12 Homework",
  "description": "This is the description of the assignment",
  "due_date": "2022-01-28T18:00:24.573Z",
  "grading_type": "points",
  "points_possible": 10,
  "category_id": "00000000-0000-0000-0000-000000000000" // homework category
}
```

#### Sample Response

The response contains the newly created **[Assignment](../models/external/assignment)** object.

```json
{
  "$data": {
    "attachments": [],
    "assignee_mode": "all",
    "grading_type": "points",
    "max_attempts": 1,
    "title": "Week 12 Homework",
    "submission_types": [
      "link"
    ],
    "state": "open",
    "points_possible": 10,
    "created_date": "2021-12-23T22:24:39.934Z",
    "updated_date": "2022-01-03T20:49:09.233Z",
    "due_date": "2022-01-28T18:00:24.573Z",
    "id": "00000000-0000-0000-0000-000000000000",
    "category_id": "00000000-0000-0000-0000-000000000000"
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## Update Assignment

### *PATCH* https://ed.link/api/v2/my/classes/:class_id/assignments/:assignment_id

Update an existing assignment in the given **[Class](../models/external/class)**.

The user must be enrolled as a `teacher`, `ta`, `designer`, `administrator`, or `district-administrator` in the class to use this endpoint.

Please review [our guide on patch requests](../../../guides/v2.0/patch-requests) for more information regarding their use.

#### Request Parameters

| Parameter       | Type     | Description                                                              |
|-----------------|----------|--------------------------------------------------------------------------|
| `class_id`      | `string` | The UUID of the desired **[Class](../models/external/class)**.           |
| `assignment_id` | `string` | The UUID of the desired **[Assignment](../models/external/assignment)**. |

#### Request Body

The request body should contain a partial **[Assignment](../models/external/assignment)** object.

The following fields are allowed: `title`, `description`, `description_plaintext`, `state`, `due_date`, `display_date`, `start_date`, `end_date`, `assignee_mode`, `assignee_ids`, `points_possible`, `grading_type`, `submission_types`, `max_attempts`, `session_id`, `category_id`.

```json
{
  "title": "Week 13 Homework"
}
```

#### Sample Response

The response contains the updated **[Assignment](../models/external/assignment)** object.

```json
{
  "$data": {
    "attachments": [],
    "assignee_mode": "all",
    "grading_type": "points",
    "max_attempts": 1,
    "title": "Week 13 Homework",
    "submission_types": [
      "link"
    ],
    "state": "open",
    "points_possible": 10,
    "created_date": "2021-12-23T22:24:39.934Z",
    "updated_date": "2022-01-03T20:49:09.233Z",
    "due_date": "2022-01-28T18:00:24.573Z",
    "id": "00000000-0000-0000-0000-000000000000",
    "category_id": "00000000-0000-0000-0000-000000000000"
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## Delete Assignment

### *DELETE* https://ed.link/api/v2/my/classes/:class_id/assignments/:assignment_id

Delete an existing assignment in the given **[Class](../models/external/class)**.

The user must be enrolled as a `teacher`, `ta`, `designer`, `administrator`, or `district-administrator` in the class to use this endpoint.

#### Request Parameters

| Parameter       | Type     | Description                                                              |
|-----------------|----------|--------------------------------------------------------------------------|
| `class_id`      | `string` | The UUID of the desired **[Class](../models/external/class)**.           |
| `assignment_id` | `string` | The UUID of the desired **[Assignment](../models/external/assignment)**. |

#### Sample Request

```javascript
axios.delete(`https://ed.link/api/v2/my/classes/${class_id}/assignments/${assignment_id}`, {
	headers: {
		authorization: `Bearer ${person_access_token}`
	}
});
```

#### Sample Response

The response is empty, with a status code of `200`.
