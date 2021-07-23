# Paginated Requests

Due to the scale of working with school data, many requests in the Edlink API have the potential to return hundreds or thousands of results. In order to handle the transfer of large amounts of data, Edlink provides a robust paging system for developers to pull data in a stable and organized manner. Virtually all requests that return multiple results can be paginated and will be marked as such in the documentation.

While ordinary paging typically involves some sort of `limit` or `offset` parameters, such a system would be highly error prone in situations where data may update at any time. If data is added or removed from page 5 while you're loading data from page 7, you might double count or even accidentally skip results. To that end, Edlink implements a cursor-based paging system. Cursors help you navigate through search results without running into issues with changing data. You can even store a cursor to pick up where you left off.

## Loading the Previous or Next Page

In addition to the `$data` parameter returned by all requests from our system, paginated requests will include `$previous` and `$next` parameters to make your development experience easier. For example, if you ask Edlink for a list of classes, you will receive a response in the following format:

```javascript
{
    $data: [
        Class,
        ...
    ]
    $previous: String,
    $next: String,
    $request: UUID
}
```

## Paging Parameters

If you prefer not to use the `$previous` and `$next` parameters, Edlink provides 4 query parameters to assist in the paging process. Two of them, `$before` and `$after`, are used to load resources immediately preceding or following the specified resource, respectively. The others, `$first` and `$last`, allow you to simultaneously sort results, and limit the number of results that are returned from a query. Paging parameters are not required, and per-request defaults will be outlined in their respective documents.

It is worth noting that most of the time, Edlink will use these parameters to generate the `$previous` and `$next` values discussed above.

#### Forward Paging

Forward paging (e.g. page 1, 2, 3...) works with a combination of the `$first` and `$after` query parameters. The `$first` indicates how many results you are looking to retrieve. The `$after` parameter is used to retrieve additional pages and can be set to any object UUID. Typically, you'll retrieve the first page, and then set the `$after` parameter to the last object ID in the set of items that you retrieved. For convenience, a `$next` value may be provided by the server which will link directly to the next page of results. The `$first` parameter may not exceed 10,000.

#### Backward Paging

Backward paging is extremely similar to forward paging but will return results in reverse order from which they were created. The `$last` parameter may not exceed 10,000.

## Caveats

* We cannot provide `$before` and `$after` paging for certain requests to the learning management system, due primarily to technical limitations of these systems
    * We will indicate in the documentation where this is the case.
    * These endpoints will use the `$count` and `$page` parameters instead.
    * These requests generally involve assignments or student submissions. 
    * This is taken into account when Edlink generates the `$previous` and `$next` parameters (they are generated correctly).

## Pagination Example

To give a concrete example, let's say we are importing a list of all of the classes that our application has access to, using the endpoint `https://ed.link/api/v2/graph/classes`. More information about this endpoint can be found at the [associated document](/docs/api/v2.0/graph/classes).

Let's say we want a page size of 100 results per page. The way to achieve this is to append a parameter of `$first=100`.

```javascript
const { $data, $next } = await axios.get(`https://ed.link/api/v2/graph/classes?$first=100`);
```

If we make an initial call to this URL, we will receive a set of up to 100 classes. Suppose, however, that we do have access to at least 100 classes, how do we access the next page?

One option is that we can simply make a request to the URL contained in the `$next` parameter.

```javascript
const next_page = await axios.get($next);
```

If we want to do this manually, we can look at the last item in the `$data` array, and take its UUID. We then append this ID to our request using the `$after` parameter.

```javascript
const $after = $data.pop().id;
const next_page = await axios.get(`https://ed.link/api/v1/graph/classes?$first=100&$after=${$after}>`);
```

This request will return the `$first` 100 results `$after` the last one received. In summary, we can continue listing pages by simply changing the `$after` parameter to the last item that we received in the previous request.

## Notes

* There is no requirement that you keep the same page size each time you make a request. Just modify the `$first` or `$last` value to reflect the number of results that you would like to receive.
* Since our "cursors" are just the ID of an element, they do not expire. A cursor will only become "invalid" if the item is subsequently deleted.