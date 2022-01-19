# Patch Requests

Particularly when modifying assignment and submission data through the User API, you'll find that many of our v2 endpoints are designed to accept a `PATCH` rather than a `PUT` method. If you're not yet familiar with `PUT`, fret not! We've put together this guide to help you understand the differences.

## How Patch and Put Differ

For the sake of the following examples, let's say we're working with the following **[Assignment](../../api/v2.0/models/external/assignment)** object, and we want to change its `title`.
```json
{
  "title": "Week 7 Astronomy Homework",
  "description": "Solve the attached problems to find the gravitational pull between various planets.",
  ...
}
```

### Put Method
**During a `PUT` request,** the user sends a JSON object that will *replace* the existing resource. This means that all fields will be overwritten, and any fields that are not included will be removed. This means it's up to the user to make sure that you don't accidentally remove important fields.

In v1, your `PUT` request body to change the `title` of the assignment might have looked like this.

`PUT https://ed.link/api/v1/my/classes/:class_id/assignments/:assignment_id`

```json
{
  "title": "Gravity Quiz", // new title
  "description": "Solve the attached problems to find the gravitational pull between various planets.",
  ...
}
```

Notice how we had to repeat the `description` property, and the rest of the properties on the object, even though we didn't change them. 

This method also has a higher propensity for side effects. If someone were to modify the description since you last retrieved the assignment, you'd be overwriting their changes with an older version.

### Patch Method

**Conversely, during a `PATCH` request,** the user sends a JSON object that will *modify* the existing resource. In Edlink's case, this means that only the fields that you provide in the request body will be modified.

In v2, your `PATCH` request body to change the `title` of the assignment might look like this instead.

`PATCH https://ed.link/api/v1/my/classes/:class_id/assignments/:assignment_id`

```json
{
  "title": "Gravity Quiz"
}
```

Notice that this time, we only had to include the property that we wanted to change. The rest of the properties on the object will remain intact.

## Using `$properties`

Edlink also provides a useful `$properties` URL parameter that allows you to specify which properties included in your response body should be processed. If you include this parameter, Edlink will ignore any properties that you don't list.

> Be careful! Don't confuse `$properties` with `$fields`, which is [documented separately here](limiting-fields). As a rule of thumb, `$properties` is for limiting input fields, and `$fields` is for limiting output fields.

### Example

We'll use the same example assignment from above to demonstrate the `$properties` parameter.

`PATCH https://ed.link/api/v2/my/classes/:class_id/assignments/:assignment_id?$properties=title`

If you want to supply multiple properties, you can provide a comma-separated list, i.e. `$properties=title,description`.

#### Request Body

```json
{
  "title": "Gravity Quiz",
  "description": "Solve the attached problems to find the gravitational pull between various planets.",
  ...
}
```

Despite providing multiple fields, only the `title` property will be processed. The rest of the properties will be ignored as if they were not sent at all.

This feature is particularly useful when language or environment limitations make it difficult to serialize partial objects into JSON.
