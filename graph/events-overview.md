<div class="card notice">
    <p>
        Although the Edlink Events API is not restricted, events must be enabled for your application. They are non-trivial to generate and therefore, we do not enable them
        by default. If you wish to use events, please contact us. If your application does not have events enabled, you will receive a 400 error.
    </p>
</div>

The events API allows you to sync only data that has changed (deltas). Events are automatically generated when people, enrollments, terms, and organizations are created, updated, or deleted. Events are scoped to a single integration

### The Event Object

| Property | Type | Description |
|---|---|---|
| `id` | UUID | A stable UUID corresponding to this event. |
| `created_date` | Date | The date this event was created. |
| `type` | String (Enum) | The object type concatenated with either `created`, `updated`, or `deleted`. |
| `data` | String | The new object as it exists after this event (unless it has been deleted). |

### Event Types

The following event types are available. Please note, more event types may be aviailable in the future. Your application should simply skip or disregard any unknown event types so it does not break if further event types are added.

| Object Type | Available Events |
|---|---|
| Terms | `term.created`, `term.updated`, `term.deleted` |
| Organizations | `organization.created`, `organization.updated`, `organization.deleted` |
| People | `person.created`, `person.updated`, `person.deleted` |
| Enrollments | `enrollment.created`, `enrollment.updated`, `enrollment.deleted` |

## List Events
### *GET* https://ed.link/api/v1/graph/events

Retrieve a list all available events. Events go back in time up to 30 days, in accordance with our data retention policy. Events should **always** be processed in the order in which they are returned. When paging through events, it is always recommended to page forward using `$first` and `$after`. While backward paging is supported, there is really no good reason to do so, and it may result in corrupted data (due to events being applied in reverse order).

#### Request Parameters

This query allows for [standard paging parameters](/docs/graph/paginated-requests).

#### Sample Request

```javascript
axios.get('https://ed.link/api/v1/events', {
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
            "id": "1ddd5890-5d37-4bc9-88da-3f5980446ab8",
            "created_date": "2020-06-19T21:27:45.349Z",
            "type": "term.updated",
            "data": {
                "id": "1c26e644-b95f-4fbd-92b5-84cd65b0ab69",
                "source": {
                    "id": "9aec5b81-fe3c-4629-a989-a75f02d9e947"
                },
                "name": "Spring Semester",
                "end_date": "2020-06-30T00:00:00+00:00",
                "sync_date": "2020-06-19T05:14:41.440089+00:00",
                "start_date": "2020-01-01T00:00:00+00:00",
                "created_date": "2020-03-02T07:36:30.86103+00:00",
                "updated_date": "2020-03-02T07:36:30.86103+00:00"
            }
        },
        { ... }
    ]
}
```

## Fetch A Single Event
### *GET* https://ed.link/api/v1/graph/events/:event\_id

Retrieve information about a specific event. You may not be able to retrieve information about events that are greater than 30 days old.

#### Request Parameters

| Parameter | Type | Description |
|---|---|---|
| `event_id` | UUID | The UUID of the desired event. |


#### Sample Request

```javascript
axios.get('https://ed.link/api/v1/events/77a69705-41a7-49cb-0fe8-ffd425f9716f', {
    headers: {
        authorization: `Bearer ${integration_access_token}`
    }
});
```

#### Sample Response

```json
{
    "$data": {
        "id": "a2a8c9ff-b0c9-42d7-9a8b-c5d07c8dd5b4",
        "created_date": "2020-06-19T22:35:04.144Z",
        "type": "person.created",
        "data": {
            "id": "3497d140-06df-4425-ad04-83ec4665fbf3",
            "source": {
                "id": "9aec5b81-fe3c-4629-a989-a75f02d9e947"
            },
            "role": "teacher",
            "email": "jordan@ed.link",
            "phone": "",
            "gender": null,
            "locale": "",
            "birthday": null,
            "last_name": "Clark",
            "sync_date": "2020-06-19T22:35:04.144928+00:00",
            "time_zone": "America/Chicago",
            "first_name": "Jordan",
            "properties": {},
            "middle_name": "",
            "picture_url": "",
            "created_date": "2020-06-19T22:35:04.144928+00:00",
            "display_name": "Jordan Clark",
            "updated_date": "2020-06-19T22:35:04.144928+00:00"
        }
    }
}
```