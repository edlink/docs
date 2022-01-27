# Errors & Warnings

## Errors
One or more **errors** will result when the API encounters a situation that it cannot gracefully handle. You'll want to look at the details of each error to determine how to address them.

Every error returned by the API will include a `code` and `message` field to aid you in remedying the problem.

Notice that multiple errors could be reported at once. This makes it possible to address multiple problems before trying to send the request again.

[You can find a list of common error codes here](../../api/v2.0/responses/errors).

We will return a response body with the following structure when any errors occur:

```json
{
  "$request": "00000000-0000-0000-0000-000000000000",
  "$errors": [
    {
      "code": "ERROR_CODE_EXAMPLE",
      "message": "This is a human-readable description of the error."
    }
  ]
}
```


## Warnings 
A **warning** results when the API wants to let you know about a situation that is not an error, but could still cause problems or unexpected results.

Like errors, every warning returned by the API will include a `code` and `message` field to aid you in remedying the problem.

[You can find a list of common warning codes here](../../api/v2.0/responses/warnings).

Warnings can be included in any API response, including alongside errors. We recommend that you monitor all responses for warnings. They appear in the following format:

```json
{
  "$request": "00000000-0000-0000-0000-000000000000",
  "$data": [ ... ],
  "$warnings": [
    {
      "code": "WARNING_CODE_EXAMPLE",
      "message": "This is a human-readable description of the warning."
    }
  ]
}
```
