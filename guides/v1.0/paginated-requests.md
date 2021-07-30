Many requests in the Edlink API have the potential to return hundreds or thousands of results. In order to cope with the transfer of large numbers of resources, Edlink provides a robust paging system for developers to pull data in a stable and organized manner. Requests that can be paginated are marked as such in the documentation.

Where ordinary paging may involve some sort of `limit` or `offset` parameters, such a system would be highly error prone in situations where data may update at any time. If data is added or removed from page 5 while you're loading data from page 7, you might double count or even accidentally skip results.

## Paging Parameters

Edlink provides 4 query parameters to assist in the paging process. Two of them, `$before` and `$after`, are used to load resources immediately preceding or following the specified resource, respectively. The others, `$first` and `$last`, allow you to simultaneously sort results, and limit the number of results that are returned from a query. Paging parameters are not required, and per-request defaults will be outlined in their respective documents.

#### Forward Paging

Forward paging (e.g. page 1, 2, 3...) works with a combination of the `$first` and `$after` query parameters. The `$first` indicates how many results you are looking to retrieve. The `$after` parameter is used to retrieve additional pages and can be set to any object UUID. Typically, you'll retrieve the first page, and then set the `$after` parameter to the last object ID in the set of items that you retrieved. For convenience, a `$next` value may be provided by the server which will link directly to the next page of results. The `$first` parameter may not exceed 10,000.

#### Backward Paging

Backward paging is extremely similar to forward paging but will return results in reverse order from which they were created. The `$last` parameter may not exceed 10,000.

## Caveats

* We cannot provide `$before` and `$after` paging for certain requests to the learning management system, due primarily to technical limitations of these systems. We will indicate in the documentation where this is the case. These endpoints will use the `$count` and `$page` parameters instead. These requests generally involve assignments or student submissions.

## Best Practices

It is highly encouraged that you only use the `$first` and `$after` parameters to page through results. There is no performance detriment to using other parameters, but you are encouraged to think carefully about the behavior you are trying to achieve, and make sure that `$last` or `$before` are indeed the correct parameters to use.

# Example

To give a concrete example, let's say we are importing a list of all of the courses that our application has access to, using the endpoint `https://ed.link/api/v1/graph/courses`. More information about this endpoint can be found at the [associated document](/docs/api/v1.0/graph/courses).

Let's say we want a page size of 100 results per page. The way to achieve this is to append a parameter of `$first=100`.

```javascript
const courses = await axios.get(`https://ed.link/api/v1/graph/courses?$first=100`);
```

If we make an initial call to this URL, we will receive a set of up to 100 courses. We may not have 100 courses if access has not been granted by a large number of schools. Suppose, however, that we do have access to at least 100 courses, how do we access the next page?

Simply, we look at the last item in the results array, and take its UUID. We then append this ID to our request using the `$after` parameter.

```javascript
const next_page = await axios.get(`https://ed.link/api/v1/graph/courses?$first=100&$after=${previous_uuid}>`);
```

This request will return the `$first` 100 results `$after` the last one received. In summary, we can continue listing pages by simply changing the `$after` parameter to the last item that we received in the previous request.
