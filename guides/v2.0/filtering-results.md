# Filtering Results

v2.0 of the Edlink API provides a robust filtering system.

## Constructing Filters

It's easier to understand what `$filter` is doing when it's fully expanded. You'll want to minify it  (strip out all the line breaks and extra spaces) before you send it to the Edlink API.

Let's say we wanted to search for all **[People](../../api/v2.0/models/external/person)** with names starting with the letter Z.

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

## Operators
This is a list of all filtering operators. Note that every operator might not be available for every property of the given type. View the appropriate model page (listed below) to see which fields are filterable using which operators.

At present, the following models support filtering. Any endpoint which returns these models supports the `$filter` parameter.

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

### Strings
#### `equals`
The field's value must equal the provided `value`. Case sensitive.

```json
{
  "operator": "equals",
  "value": "Chris"
}
```

#### `starts_with`

| Operator | Description |
| -------- | ----------- |
| `starts with` | The field's value must start with the provided `value`. Case insensitive. |
| `contains` | The field's value must contain the provided `value`. Case insensitive. |
| `in` | The field's value must exist within the provided `value`. Case sensitive. |
| `not in` | The field's value must not exist within the provided `value`. Case insensitive.
