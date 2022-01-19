# Limiting Response Fields

For your convenience, Edlink provides a handy parameter, `$fields`, to reduce the amount of data coming from an API request. When you attach this query parameter to the end of your API request, Edlink will trim the response body to contain *only* the requested fields. You may want to make use of this parameter for several reasons including:

* It may reduce request latency and bandwidth requirements between your servers and Edlink, due to a reduction in the overall amount of data sent across the wire.
* It may help you insulate yourself from unwanted student data. For example, if your platform does not require an email address field for users, you can eliminate it from the response body to prevent exposure.

## The `$fields` Parameter

The `$fields` parameter is a standard query parameter that accepts a comma-separated list of field names. The values allowed in the list vary by API request. Any invalid values will be ignored and a warning will be issued in the response body `$warnings` array.

The `$fields` parameter is available for both Graph API requests and User Data API requests.

## Example

Let's say we wanted to list all [`People`](../../api/v2.0/models/external/person) at a given district or university, but we did not want to receive all of the metadata that Edlink stores about a `Person` in the API response. In this case, we might only want to list their Edlink ID, first name, and last name. The request URL would be as follows:

`GET https://ed.link/api/v2/graph/people?$fields=id,first_name,last_name`

Note, the `$fields` query parameter is a list of comma-separated values. The response body will contain only those fields:

```json
{
    "$data": [
        {
            "id": "85558ad0-34c7-44f4-bcac-30f11221f920",
            "first_name": "John",
            "last_name": "Smith"
        },
        {
            "id": "1b094165-02b5-4962-a1b1-3cee3aa1622b",
            "first_name": "Alice",
            "last_name": "Roberts"
        },
        ...
    ]
    ...
}
```
