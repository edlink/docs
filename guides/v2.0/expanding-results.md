# Expanding Results

v2.0 of the Edlink API provides a robust expansion system. This system allows you to pull related objects from the Edlink API without having to make many separate requests.

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
