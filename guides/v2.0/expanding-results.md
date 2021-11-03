# Expanding Results

v2.0 of the Edlink API provides a robust expansion system. This system allows you to pull related objects from the Edlink API without having to make several individual requests.

For instance... <!-- todo probably an example about agents or enrollments, any situation where the point of interest is probably not the join object -->

Expanding works by using the `$expand` URL parameter against endpoints that support it. Typically, any endpoint that returns an array in `$data` can be expanded.

Without expansion, you would have to make a separate request for each **Agent** in the array.

```json
{
  "id": "00000000-0000-0000-0000-000000000000",
  "relationship": "guardian",
  "observer_id": "00000000-0000-0000-0000-000000000000",
  "target_id": "00000000-0000-0000-0000-000000000000"
}
```

Using expansion, you can retrieve the details of each **Agent**'s `observer` with one request.

```json
{
  "id": "00000000-0000-0000-0000-000000000000",
  "relationship": "guardian",
  "observer_id": "00000000-0000-0000-0000-000000000000",
  "observer": {
    "id": "00000000-0000-0000-0000-000000000000",
    "first_name": "George",
    "middle_name": "Oscar",
    "last_name": "Bluth",
    ...
  },
  "target_id": "00000000-0000-0000-0000-000000000000"
}
```

## Expandable Fields

As a general rule of thumb, most fields that end in `_id` or `_ids` can be expanded. For example, `school_ids` on a **Person** can be expanded with `$expand=schools` to return the `schools` array.

View the appropriate model page (listed below) to see which fields are expandable. Any endpoint which returns these models supports the `$expand` parameter.

* [People](../../api/v2.0/models/external/person)
* [Schools](../../api/v2.0/models/external/school)
* [Classes](../../api/v2.0/models/external/class)
* [Sections](../../api/v2.0/models/external/section)
* [Sessions](../../api/v2.0/models/external/session)
* [Enrollments](../../api/v2.0/models/external/enrollment)
* [Agents](../../api/v2.0/models/external/agent)
* [Courses](../../api/v2.0/models/external/course)
