# Events API

Using Edlink's [Events API](../../api/v2.0/graph/events), you can observe incremental changes in provider data over
time. Using this data, you can make updates to your own database. We typically call this procedure a "hot sync". This is in contrast to a "full sync" which would constitute fetching *all* of the data from the provider.

> You should note that events go back in time only up to 30 days, in accordance with our data retention policy. Events older than 30 days are subject to deletion, and **cannot be recovered**. For this reason (among others) it's important that you can also support a "full sync" with Edlink.
>
> [You can read more about how to perform a "full sync" here.](class-rostering)

## Nightly Syncs

Many of our clients opt to perform this procedure on a nightly basis to see what's changed in the data source over the
course of the day.

In order to do this, we'll paginate through the [events endpoint](../../api/v2.0/graph/events) to see what's changed
since we last checked. The endpoint will return events in chronological order.

[The format of event objects received into the `processEvent` function of this example code is described here.](../../api/v2.0/models/internal/event)

```javascript
// Create an axios request config with our token
// (Remember, it should never actually be hard-coded like this)
const config = {
	headers: {
		'Authorization': 'Bearer XxYUqqrxHBo6yWBqcry8b73GhibnrQyq'
	}
};

// Should be set to the id of the last event you've processed
// We'll be looking at the events that occurred after this one
const after = '00000000-0000-0000-0000-000000000000';

// This field will hold the url for our next request
// We'll get 10000 items at a time for maximum efficiency
let url = `https://ed.link/api/v2/graph/events?$first=10000&$after=${after}`;

// While our url is not undefined or empty
while (url) {
	// Wait for the result of the api call to Edlink
	const result = await axios.get(url, config).then(res => res.data);

	// Loop through the events contained in the response
	for (const event of result.$data) {

		// Write a function to process events as they come in
		await processEvent(event);

		// Make sure you record the id of the last event you've
		// processed, so that it can be set as the `after` const
		// next time this code runs.
	}

	// Set the url variable so we get the next page on the next loop
	// If $next is undefined, our pagination is over & the loop will end
	url = result.$next;
}
```
