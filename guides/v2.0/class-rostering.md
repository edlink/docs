# Class Rostering

Using Edlink's Graph API, you can extract mass amounts of provider data at a time, and use it to populate your own database. We typically call the procedure of retrieving *all* of the data for an integration a "full sync."

> You'll want to make sure you've read the "Graph API Authorization" section of the [authorization guide](authorization) to prepare to fetch data from Edlink.
>
> You may also want to reference our [paginated requests guide](paginated-requests) to understand some of the URL parameters that you'll see me use in this guide.

## Extracting Data

In order to extract data, we'll paginate through various endpoints in the Graph API that correspond to each of our primary external data models.

```javascript
// Create an axios request config with our token
// (Remember, it should never actually be hard-coded like this)
const config = {
	headers: {
		'Authorization': 'Bearer XxYUqqrxHBo6yWBqcry8b73GhibnrQyq'
	}
};

// Create an array to hold all of our schools
const schools = [];

// This field will hold the url for our next request
// We'll get 10000 items at a time for maximum efficiency
let url = 'https://ed.link/api/v2/graph/schools?$first=10000';

// While our url is not undefined or empty
while (url) {
	// Wait for the result of the api call to Edlink
	const result = await axios.get(url, config).then(res => res.data);

	// Push all of the resulting data to our schools array
	schools.push(...result.$data);

	// Set the url variable so we get the next page on the next loop
	// (If $next is undefined, our pagination is over & the loop will end)
	url = result.$next;
}

// At this point, you'll have all of your integration's schools
// stored in the schools array. Rinse and repeat for all of the
// other data model types.
```

If you're performing a full sync, it's recommended to access the school data models in the following order:

1. [District](../../api/v2.0/models/external/district) [`https://ed.link/api/v2/graph/districts`](../../api/v2.0/graph/districts)
1. [School](../../api/v2.0/models/external/school) [`https://ed.link/api/v2/graph/schools`](../../api/v2.0/graph/schools)
1. [Session](../../api/v2.0/models/external/session) [`https://ed.link/api/v2/graph/sessions`](../../api/v2.0/graph/sessions)
1. [Course](../../api/v2.0/models/external/course) [`https://ed.link/api/v2/graph/courses`](../../api/v2.0/graph/courses)
1. [Person](../../api/v2.0/models/external/person) [`https://ed.link/api/v2/graph/people`](../../api/v2.0/graph/people)
1. [Class](../../api/v2.0/models/external/class) [`https://ed.link/api/v2/graph/classes`](../../api/v2.0/graph/classes)
1. [Section](../../api/v2.0/models/external/section) [`https://ed.link/api/v2/graph/sections`](../../api/v2.0/graph/sections)
1. [Enrollment](../../api/v2.0/models/external/enrollment) [`https://ed.link/api/v2/graph/enrollments`](../../api/v2.0/graph/enrollments)
1. [Agent](../../api/v2.0/models/external/agent) [`https://ed.link/api/v2/graph/agents`](../../api/v2.0/graph/agents)

We recommend this order because it ensures that, for example, a class will be loaded before an enrollment ever depends on it.
