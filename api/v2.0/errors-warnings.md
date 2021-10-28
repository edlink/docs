# Errors & Warnings

## Errors
An **error** results when the API encounters a situation that it cannot handle.

Every error returned by the API will include a `$code` and `$description` field to aid you in remedying the problem.

We will return a `500` response code and a response body with the following structure when any errors occur.
```json
{
  "$request": "00000000-0000-0000-0000-000000000000",
  "$errors": [
    {
      "$code": "ERROR_EXAMPLE",
      "$description": "This is a human-readable description of the error."
    }
  ]
}
```

## Warnings 
A **warning** results when the API wants to let you know about a situation that is not an error, but could still cause problems or unexpected results.

Like errors, every warning returned by the API will include a `$code` and `$description` field to aid you in remedying the problem.

Warnings can be included in any API response, including errors. We recommend that you monitor all responses for warnings.

```json
{
  "$request": "00000000-0000-0000-0000-000000000000",
  "$data": [ ... ],
  "$warnings": [
    {
      "$code": "WARNING_EXAMPLE",
      "$description": "This is a human-readable description of the warning."
    }
  ]
}
```
