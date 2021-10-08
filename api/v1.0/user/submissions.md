# Submissions

## Listing Submissions for an Assignment
### *GET* https://ed.link/api/v1/my/courses/:course\_id/assignments/:assignment\_id/submissions

For a given assignment in a given course, return a list of the student submissions. This endpoint may vary slightly by LMS as different systems handle submissions in different ways. However, for most use cases, this small variance should not be a problem, or affect your usage of this API.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `course_id` | URL Parameter | The UUID for the course from which you want to retrieve assignments. |
| `assignment_id` | URL Parameter | The ID of the assignment that you want to retrieve submissions for. |

This request also allows for the [modified paging parameters](/docs/guides/v1.0/paginated-requests).

#### Response Data

This endpoint returns an array of `Submission` objects. Students will only receive their own submission object.

#### Sample Request

``` javascript
axios.get('https://ed.link/api/v1/my/courses/8ab9c040-d458-4746-9bea-99f4b5066f17/assignments/74de393e-a5bc-43ee-b431-7826dfc59300/submissions', {
    headers: {
        'Authorization': `Bearer ${user_access_token}`
    }
});
```

## Fetching a Single Submission
### *GET* https://ed.link/api/v1/my/courses/:course\_id/assignments/:assignment\_id/submissions/:submission\_id

Retrieve a single student submission to an assignment. This endpoint can be accessed by either:

* The student who originally created the submission, or
* Any person who has a `teacher`, `ta`, or `administrator` enrollment in the relevant course.

| Parameter | Type | Description |
|---|---|---|
| `course_id` | URL Parameter | The UUID for the course from which you want to retrieve assignments. |
| `assignment_id` | URL Parameter | The ID of the assignment that corresponds to this submission. |
| `submission_id` | URL Parameter | The ID of the submission that you want to retrieve. |

#### Response Data

This endpoint returns a `Submission` object.

#### Sample Request

``` javascript
axios.get('https://ed.link/api/v1/my/courses/8ab9c040-d458-4746-9bea-99f4b5066f17/assignments/74de393e-a5bc-43ee-b431-7826dfc59300/submissions/cba2306c-d2a5-420e-9b2f-715f53788885', {
    headers: {
        'Authorization': `Bearer ${user_access_token}`
    }
});
```

## Creating an Assignment Submission
### *POST* https://ed.link/api/v1/my/courses/:course\_id/assignments/:assignment\_id/submissions

Create a new submission for an assignment or quiz resource. This endpoint is only available to people who are enrolled as students in the current course.

| Parameter | Type | Description |
|---|---|---|
| `course_id` | URL Parameter | The UUID for the course from which you want to retrieve assignments. |
| `assignment_id` | URL Parameter | The ID of the assignment that corresponds to this submission. |

#### Request Body

A `Submission` object is expected in the request body.

#### Response Data

This endpoint returns the newly created `Submission` object.

#### Sample Request

``` javascript
axios.post('https://ed.link/api/v1/my/courses/8ab9c040-d458-4746-9bea-99f4b5066f17/assignments/74de393e-a5bc-43ee-b431-7826dfc59300/submissions', {
    body: 'Submission Body'
},
{
    headers: {
        'Authorization': `Bearer ${user_access_token}`
    }
});
```

## Updating an Assignment Submission

There is no endpoint to update an assignment submission, as this is not possible in most LMS systems. However, you can call the `POST` endpoint multiple times in order to create multiple submissions for a single user. These will be indicated as multiple "attempts" within the source system.

## Grading an Assignment Submission
### *PUT* https://ed.link/api/v1/my/courses/:course\_id/assignments/:assignment\_id/submissions/:submission\_id/grade

This endpoint updates the score of a student's submission.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `course_id` | URL Parameter | The UUID for the course from which you want to retrieve assignments. |
| `assignment_id` | URL Parameter | The ID of the assignment that you want to grade. |
| `submission_id` | URL Parameter | The ID of the submission that you want to grade. |

#### Request Body

| Parameter | Type | Description |
|---|---|---|
| `score` | Number | The student's score for this submission. |

#### Response Data

This endpoint returns `200 OK` if the submission was successfully graded.

#### Sample Request

``` javascript
axios.put('https://ed.link/api/v1/my/courses/8ab9c040-d458-4746-9bea-99f4b5066f17/assignments/74de393e-a5bc-43ee-b431-7826dfc59300/submissions/cba2306c-d2a5-420e-9b2f-715f53788885', {
    headers: {
        'Authorization': `Bearer ${user_access_token}`
    }
});
```