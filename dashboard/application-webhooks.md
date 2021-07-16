Webhooks allow Edlink to alert you of certain events that impacted your application. When one of these events are triggered, we will send you a payload to your webhook endpoint that describes the success or failure of the event.

You can access your Webhook Signing Secret by selecting ***Applications*** from the navigation header, choosing an application from the list under *Application*, and selecting ***Webhooks*** from the navigation sidebar. This page will also allow you to set your Webhook Endpoint and select which Webhook Events you wish to enable. Be sure to save your Endpoint and Webhook Events when finished.

![webhook](/documentation/media/dashboard/dev/webhooks.jpg)

The Webhook Events Edlink supports include:

- **Import Started**: Fired when an import has been queued for an integrated source.
- **Import Working**: Fired when an import has started for an integrated source.
- **Import Complete**: Fired when an import has successfully completed.
- **Import Error***: Fired when an import has been terminated due to an error.
- **Import Canceled**: Fired when an import has canceled automatically due to server restart.
- **Import Killed**: Fired when an import has been canceled by an administrator.
