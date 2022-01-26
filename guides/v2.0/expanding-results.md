# Expanding Results

v2.0 of the Edlink API provides a robust expansion system. This system allows you to pull related objects from the Edlink API without having to make several individual requests.

For instance, when retrieving a list of **[Agents](../../api/v2.0/models/external/agent)**, it's likely that you're mostly interested in the **[People](../../api/v2.0/models/external/person)** attached to them.

Without expansion, you would have to make a separate request for each **[Agent](../../api/v2.0/models/external/agent)** in the array to get the information you're looking for. Instead, you can get all of this information in a single request using expansion.

Let's look at an example, starting with a basic call to retrieve a list of **[Agents](../../api/v2.0/models/external/agent)**.

```
GET https://ed.link/api/v2/my/agents
```
```json
{
  "id": "00000000-0000-0000-0000-000000000000",
  "relationship": "guardian",
  "observer_id": "00000000-0000-0000-0000-000000000000",
  "target_id": "00000000-0000-0000-0000-000000000000"
}
```

To use expansion, provide the `$expand` parameter. With this method, you can retrieve the details of each **[Agent](../../api/v2.0/models/external/agent)**'s `observer` with one request.

```
GET https://ed.link/api/v2/my/agents?$expand=observer
```
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

As you can see, the `observer` property is added containing the data for the **[Person](../../api/v2.0/models/external/person)** who is the `observer` of each **[Agent](../../api/v2.0/models/external/agent)**.

## Expandable Fields

As a general rule of thumb, most fields that end in `_id` or `_ids` can be expanded. For example, `school_ids` on a **Person** can be expanded with `$expand=schools` to include the `schools` array.

View the appropriate model page (listed below) to see which fields are expandable. Any endpoint which returns these models supports the `$expand` parameter.

* **Rostering**
  * [People](../../api/v2.0/models/external/person)
  * [Schools](../../api/v2.0/models/external/school)
  * [Classes](../../api/v2.0/models/external/class)
  * [Sections](../../api/v2.0/models/external/section)
  * [Sessions](../../api/v2.0/models/external/session)
  * [Enrollments](../../api/v2.0/models/external/enrollment)
  * [Agents](../../api/v2.0/models/external/agent)
  * [Courses](../../api/v2.0/models/external/course)
* **Class Content**
  * [Categories](../../api/v2.0/models/external/category)
  * [Assignments](../../api/v2.0/models/external/assignment)
  * [Submissions](../../api/v2.0/models/external/submission)
