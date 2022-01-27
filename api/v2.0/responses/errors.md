# Error Responses

This page contains a list of common error responses you might come across while using the Edlink API. For a breakdown of how to process error responses, [check out our guide on errors and warnings](../../../guides/v2.0/errors-warnings).

> This page is under construction. User API v2 is in beta and is subject to change.

## Edlink Error Codes

### `400` UNKNOWN

The server encountered an unexpected condition which prevented it from fulfilling the request.

### `400` INTERNAL

The server encountered an unexpected condition which prevented it from fulfilling the request.

### `400` UNKNOWN_PROVIDER

Edlink could not find the proper provider for the authenticated person or integration.

### `400` INVALID_TOKEN

You must supply a valid access token to access this endpoint. Make sure that you're using the correct type of access token for the endpoint you're trying to access.

### `400` EXPIRED_TOKEN

The token you provided, while it was valid at some point, is now expired.

### `400` UNSHARED_TOKEN

The person that this token is associated with is no longer shared with the integration. You should adjust your sharing rules to allow this person to access the integration.

### `400` INVALID_PROVIDER_TOKEN

The person that the token belongs to has not signed in to Edlink with their provider account, or their provider tokens have expired, in which case they should sign out and back in again.

### `400` INVALID_INTEGRATION_STATE

The integration associated with the provided access token is not in the correct state to perform the requested action. You must set the integration to `active` or `paused`.

### `400` INVALID_UUID

You have provided a UUID in an invalid format. UUIDs must be in the UUID v4 format `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`, where each x is a hexadecimal digit. All Edlink IDs are valid v4 UUIDs.

### `400` UNSUPPORTED_OPERATION

The current provider does not support the requested operation.

### `400` NOT_FOUND

The requested resource could not be found.

### `400` NO_PERMISSION

The person that the token belongs to does not have permission to perform the requested action.

### `400` IDEMPOTENCY_KEY_TOO_LONG

The supplied `$idempotency` key may not be longer than 255 characters. [Please review our guide on idempotency](../../../guides/v2.0/idempotency).

### `400` INVALID_CURSOR

The supplied cursor is invalid. [Please review our guide on pagination](../../../guides/v2.0/paginated-requests).

### `400` INVALID_PAGE_SIZE

For rostering endpoints, the requested page size must be between `1` and `10000`. For other endpoints, the maximum page size varies based on the current provider. Omit the `$first` parameter to use the default page size. [Please review our guide on pagination](../../../guides/v2.0/paginated-requests).

### `400` ENTITY_NOT_PRESENT_IN_SOURCE

The current user or class is not present in the source system. This typically occurs when the user or class is only present in the source through data enrichment. For instance, a user who is only present in the SIS, but does not have a matching profile in the LMS.

### `400` INVALID_SUBMISSION_TYPE

One or more `submission_types` are invalid.

### `400` MISSING_REQUIRED_FIELD

One or more required fields are missing.

### `400` INVALID_ASSIGNEES

One or more `assignee_ids` must be provided when the `assignee_mode` is `individual`. Each ID should be that of a [Person](../models/external/person). The `assignee_ids` must be valid Edlink IDs, and they must all be enrolled in the associated class.
