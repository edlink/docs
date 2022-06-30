# Ensuring Idempotency

The Edlink API suppports idempotency for safely retrying requests without accidentally performing the same operation twice. This is useful when an API call is disrupted in transit and you do not receive a response. For example, if a request to [create a new assignment](../../api/v2.0/user/assignments) does not respond due to a network connection error, you can retry the request with the same idempotency key to guarantee that only one assignment is created.

If the original request was successful (i.e. the assignment was created in the LMS) but ended in a network error, you can safely replay the request using the same idempotency key. This subsequent request *will not* create a duplicate assignment, but *will* return the API response you should have received initially - had the network error never occurred.

## Performing an Idempotent Request

To perform an idempotent request, simply provide an additional query parameter called `$idempotency`. This query parameter should be a short and sufficiently random string, so as to not accidentally conflict with any prior requests. Idempotency requests remain in force for 30 days, after which they are discarded and can theoretically be reused (although they probably shouldn't be anyway).

Only `POST` requests may contain idempotency keys. If you attempt to send one on another request type, Edlink will ignore the value and return a [warning](errors-warnings). Only `POST` requests have the potential to cause a duplicate action to be taken. All `PATCH` requests in Edlink are naturally idempotent, so replaying them will not yeild a new result.

## Generating an Idempotency Key

You can use any random string as your idempotency key. We recommend using either a UUID or random string generator, rather than rolling-your-own random value. We *do not* recommending using a timestamp as an idempotency key as these can easily conflict.

## Example Request

```javascript
axios.get('https://ed.link/api/v2/user/classes/44e54203-d4d9-4eb5-8b05-60fd4539100d/assignments', {
	headers: {
		authorization: `Bearer ${user_access_token}`
	},
    params: {
        $idempotency: 'RfOScIg0JwGS5M7MPS6vCvGlDKkbj3Qc'
    },
    data: {
        ...
    }
});
```
