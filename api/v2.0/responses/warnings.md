# Warning Responses

This page contains a list of common warnings you might come across while using the Edlink API. For a breakdown of how to process warnings, [check out our guide on errors and warnings](../../../guides/v2.0/errors-warnings).

### `PAGING_IGNORED`

When the `$cursor` parameter is used, it overrides all other paging parameters. We recommend using the `$next` url exactly as it comes out of the Edlink API, without any adjustments. [Please review our guide on pagination](../../../guides/v2.0/paginated-requests).

### `PROVIDER_IGNORED_PAGE_SIZE`

Some providers may not respect the `$first` parameter. [Please review our guide on pagination](../../../guides/v2.0/paginated-requests).

### `IDEMPOTENCY_KEY_REPEATED`

This warning is triggered when you use the same `$idempotency` key more than once. We'll return the exact same response that we did the previous time you used the given `$idempotency` key. [Please review our guide on idempotency](../../../guides/v2.0/idempotency).

### `IDEMPOTENCY_KEY_IGNORED`

The provided `$idempotency` key is ignored by Edlink when the endpoint is already idempotent. There is no harm in providing one anyway, but it won't be used. [Please review our guide on idempotency](../../../guides/v2.0/idempotency).

### `ASSIGNEES_IGNORED`

When the `assignee_mode` is set to `all`, the value of the `assignee_ids` field is ignored. 

### `INVALID_EXPANSION`

Only certain fields are allowed to be `$expand`ed. [Please review our guide on expanding results](../../../guides/v2.0/expanding-results).

### `INVALID_PATCH_PROPERTY`

Only certain fields are allowed to be specified using `$properties`. [Please review our guide on patch requests](../../../guides/v2.0/patch-requests).

### `INVALID_FIELD_REQUESTED`

Only certain fields (the ones that we provide) are allowed to be requested using `$fields`. [Please review our guide on limiting fields](../../../guides/v2.0/limiting-fields).

### `COULD_NOT_FIND_ID`

One or more `person_id`s specified in the request could not be found. Please note that the search area only includes people who are enrolled in the class related to your request. For instance, you cannot assign an assignment to a person who is not enrolled in the class.

### `FOUND_UNEXPECTED_FIELD`

You've included a field in the request body that we don't know how to handle. It will be ignored.

### `DATETIME_MISSING_TIMEZONE`

You've included a date without a timezone. We'll assume you mean UTC. [Please review our guide on dates](../../../guides/v2.0/dates).
