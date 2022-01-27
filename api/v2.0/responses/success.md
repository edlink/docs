# Successful Responses

Successful responses return an HTTP status code of `200` and, where applicable, a payload containing the requested data. 

## Response Properties

| Property   | Description                                                                                                                                     |
|------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| `$data`    | The actual response data.                                                                                                                       |
| `$request` | The UUID of the request. If you ever need to contact us regarding the API, it's helpful to include this UUID so we can investigate more easily. |
| `$count`   | The number of items in the response, if applicable.                                                                                             |

## Example Responses

When requesting a single result: 
```json
{
  "$data": {
    ...
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

When requesting multiple results: 
```json
{
  "$data": [
    {
      ...
    },
    {
      ...
    }
  ],
  "$request": "00000000-0000-0000-0000-000000000000",
  "$count": 2
}
```
