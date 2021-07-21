# Event

Whenever an item in our database changes, we generate an event. We are working with large datasets and it is much easier for developers to stay in sync with Edlink when we provide a list of deltas (i.e. changes) to indicate what has changed. For integrations where the sharing is set to "rules", events will be automatically generated when items come in and out of "visibility" to the developer. For example, sharing a new person will result in a `person.created` event, even though the person may have already existed in the Edlink database. If that same person is unshared, Edlink will generate a `person.deleted` event and the user will no longer be visible to the developer - even though Edlink is still aware of this user.

Edlink stores events in chronological order and retains them for up to 30 days, after which they are permenantly destroyed.

## Properties

| Property | Type | Description |
|---|---|---|
| `id` | UUID | A stable UUID representing this event. |
| `type` | EventType | The type of this event, joined with the type of object that this event represents (e.g. a person). For example, `person.created` or `organization.deleted`. |
| `created_date` | Date | The date this event was generated. |
| `data` | Organization, Term, Person, or Enrollment | The body of the object **after** it was modified. The exception to this is on `deleted` events; you will see the item as it last existed prior to deletion. See the specific models for more details about what properties are available. |

## JSON Example
```json
{
    "id": "237704e0-4f6d-49c3-9d39-1bbb1105d721",
    "type": "organization.created",
    "data": {
        "id": "9deba326-97b5-447a-8f42-7b53183cbbbd",
        "name": "Edlink University",
        "locale": null,
        "location": null,
        "time_zone": "America/Denver",
        "properties": {},
        "created_date": "2021-07-13T18:24:51.657262+00:00",
        "updated_date": "2021-07-13T18:24:51.657262+00:00",
        "source": {
            "id": "5d149266-95d2-42cf-8660-8b528b3bfba3"
        },
        "type": "district",
        "entity": null,
        "state": "active",
        "icon_url": null,
        "parent_id": null,
        "parent_type": null
    },
    "created_date": "2021-07-13T18:24:51.657Z"
}
```
