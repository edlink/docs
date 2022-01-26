# Quickstart

This guide will teach you how to set up a quick Node.js application to load a list of schools and the students that
belong to them. This guide requires a basic understanding of Node.js and the Javascript language.

## 1. Getting the Access Token

Each **[Integration](/docs/api/v2.0/models/internal/integration)** has its own **Access Token**. Open the integration
you want to view data for in the Edlink Dashboard, and find the **Access Token** field under **Integration Summary**.
Keep this token on hand for the next steps.

> Please read our [security guide](security) for tips on keeping sensitive data, like your access tokens, secure.

## 2. Configure Axios

We'll configure [`axios`](https://www.npmjs.com/package/axios) to make the request. This is
a [popular npm package](https://www.npmjs.com/package/axios) we use in most of our docs.

```javascript
// Import the axios package
const axios = require('axios');

// You should set this variable to your access token from step 1
const access_token = '...';

// Create our request configuration
const config = {
	headers: {
		'Authorization': `Bearer ${access_token}`
	}
}
```

## 3. Make Requests

Now that we've configured everything we need, we can make some requests. We're going to use pagination to fetch all of
the schools stored for this integration in Edlink.

> Our guides on [paginated requests](paginated-requests) and [class rostering](class-rostering) expand further on the following code samples. Check them out for more possible implementations and approaches.

```javascript
// Create an array to store the schools we find
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

// Print out how many schools we found
console.log(schools.length);
```

Now that we've assembled a list of all the schools, we can build a list of students for each of them.

```javascript
// For every school that we found
for (const school of schools) {

	// Print out the name of the school
	console.log(school.name);

	// This field will hold the url for our next request
	// We'll get 10000 items at a time for maximum efficiency
	let url = `https://ed.link/api/v2/graph/schools/${school.id}/students?$first=10000`;

	// While our url is not undefined or empty
	while (url) {
		// Wait for the result of the api call to Edlink
		const result = await axios.get(url, config).then(res => res.data);

		// Print out the display names of the students
		for (const student of result.$data) {
			console.log(` - ${student.display_name}`);
		}

		// Set the url variable so we get the next page on the next loop
		// If $next is undefined, our pagination is over & the loop will end
		url = result.$next;
	}
}
```

By the end of this exercise, your output would look something like this:

```text
1
Springfield Elementary School
 - Bart Simpson
 - Lisa Simpson
 - <...>
```
