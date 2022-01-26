# Filtering Results

v2.0 of the Edlink API provides a robust filtering system. Filtering works by using the `$filter` URL parameter against endpoints that support it. Typically, any Graph API endpoint that returns an array in `$data` can be filtered.

## Constructing a Filter

It's easier to understand what `$filter` is doing when it's fully expanded. You'll want to minify it  (strip out all the
line breaks and extra spaces) before you send it to the Edlink API.

Let's say we wanted to search for all **[People](../../api/v2.0/models/external/person)** whose `first_name` starts
with the letter `z`. The filter is composed of several parts. For each field you want to filter against, you should add a list containing each operator you want to apply to the field. 

```json
{
  "first_name": [
    {
      "operator": "starts with",
      "value": "z"
    }
  ]
}
```

A full list of available operators with examples attached and instructions to determine which operators are applicable can be found in the following Operators section.

Let's try a more complex filter. Let's find all **[People](../../api/v2.0/models/external/person)** with the first
name `Sofia` that have an email address that matches our criteria.

```json
{
  "first_name": [
    {
      "operator": "equals",
      "value": "Sofia"
    }
  ],
  "email": [
    {
      "operator": "starts with",
      "value": "sofia."
    },
    {
      "operator": "contains",
      "value": "@example.com"
    }
  ]
}
```

As this example demonstrates, multiple operators can be applied to the same field.

Let's see an example of how to make a request using a filter in code.

```javascript
// List up to 5 people whose display_name starts with A
axios.get('https://ed.link/api/v2/graph/people', {
  headers: {
    authorization: `Bearer ${integration_access_token}`
  },
  params: {
    $filter: JSON.stringify({
      display_name: [
        {
          operator: 'starts with',
          value: 'A'
        }
      ]
    }),
    $first: 5
  }
});
```

## Operators

This is a list of all filtering operators. Note that every operator might not be available for every property of the
given type. View the appropriate model page (listed below) to see which fields are filterable using which operators.

At present, the following models support filtering. Any endpoint which returns these models supports the `$filter`
parameter.

* External
    * [People](../../api/v2.0/models/external/person)
    * [Schools](../../api/v2.0/models/external/school)
    * [Classes](../../api/v2.0/models/external/class)
    * [Sections](../../api/v2.0/models/external/section)
    * [Sessions](../../api/v2.0/models/external/session)
    * [Enrollments](../../api/v2.0/models/external/enrollment)
    * [Agents](../../api/v2.0/models/external/agent)
    * [Courses](../../api/v2.0/models/external/course)
* Internal
    * [Sources](../../api/v2.0/models/internal/source)
    * [Syncs](../../api/v2.0/models/internal/sync)
    * [Materializations](../../api/v2.0/models/internal/materialization)

### `equals`

The field's value must equal the provided `value`. Case sensitive.

```json
{
  "operator": "equals",
  "value": "Chris"
}
```

### `starts with`

The field's value must start with the provided `value`. Case insensitive.

```json
{
  "operator": "starts with",
  "value": "chr"
}
```

### `contains`

The field's value must contain the provided `value`. Case insensitive.

```json
{
  "operator": "contains",
  "value": "test"
}
```

### `in`

The field's value must exactly match one of the comma-separated provided `value`s. Case sensitive.

```json
{
  "operator": "in",
  "value": "a,set,of,comma,separated,values"
}
```

### `not in`

The field's value must not exactly match any of the comma-separated provided `value`s. Case sensitive.

```json
{
  "operator": "not in",
  "value": "some,other,comma,separated,values"
}
```

### `is known`

The field's value must not be `null`.

```json
{
  "operator": "is known"
}
```

### `is unknown`

The field's value must be `null`.

```json
{
  "operator": "is unknown"
}
```

### `gt`

The field's value must be greater than the provided `value`.

```json
{
  "operator": "gt",
  "value": "2021-07-13T17:45:40.486Z"
}
```

### `gte`

The field's value must be greater than or equal to the provided `value`.

```json
{
  "operator": "gte",
  "value": "2021-07-13T17:45:40.486Z"
}
```

### `lt`

The field's value must be less than the provided `value`.

```json
{
  "operator": "lt",
  "value": "2021-07-13T17:45:40.486Z"
}
```

### `lte`

The field's value must be less than or equal to the provided `value`.

```json
{
  "operator": "lte",
  "value": "2021-07-13T17:45:40.486Z"
}
```
