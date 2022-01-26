# Paginated Requests

Due to the scale of working with school data, many requests in the Edlink API have the potential to return hundreds or thousands of results. In order to handle the transfer of large amounts of data, Edlink provides a robust paging system for developers to pull data in a stable and organized manner. Virtually all requests that return multiple results can be paginated and will be marked as such in the documentation.

While ordinary paging typically involves some sort of `limit` or `offset` parameters, such a system would be highly error-prone in situations where data may update at any time. If data is added or removed from page 5 while you're loading data from page 7, you might double count or even accidentally skip results. To that end, Edlink implements a cursor-based paging system. Cursors help you navigate through search results without running into issues with changing data.

## Loading the Next Page

In addition to the `$data` parameter returned by all requests from our system, paginated requests will include a `$next` parameter to make your development experience easier. For example, if you ask Edlink for a list of classes, you will receive a response in the following format:

```javascript
{
    $data: [
        Class,
        ...
    ],
    $next: String,
    $count: Number,
    $request: UUID
}
```

The `$next` parameter will contain a URL that can be used to load the next page of results. If there are no more pages to load, this parameter will not be present.

To give a concrete example, let's say we are importing a list of all classes that our application has access to, using the endpoint `https://ed.link/api/v2/graph/classes`. More information about this endpoint can be found in the [associated document](/docs/api/v2.0/graph/classes).

Let's say we want a page size of 100 results per page. The way to achieve this is to append a parameter of `$first=100`. Any parameter you append will affect all following pages.

```javascript
const { $data, $next } = await axios.get(`https://ed.link/api/v2/graph/classes?$first=100`);
```

If we make an initial call to this URL, we will receive a list of up to 100 classes. Suppose, however, that we do have access to at least 100 classes.

We can continue listing pages by simply using the `$next` parameter that we received from the previous request as the new URL. Please note that the `$next` parameter will only be present if there are more pages to load.

```javascript
const next_page = await axios.get($next);
```

**This is the preferred way to paginate results.**

> You may notice that the provided `$next` URL is missing some of your query parameters. Do not fret! Edlink's `$cursor` stores all the information necessary for Edlink to understand those parameters.
>
> For example, if you provide a `$filter` parameter to the first page, it will still affect the following pages, even though it isn't included in the `$next` URL.

## Additional Graph Paging Parameters

If you prefer not to use the `$next` parameter, Edlink provides 4 query parameters to assist in the paging process. Two of them, `$before` and `$after`, are used to load resources immediately preceding or following the specified resource, respectively. The others, `$first` and `$last`, allow you to simultaneously sort results, and limit the number of results that are returned from a query.

An alternate strategy for pagination involves a combination of the `$first` and `$after` query parameters. The `$first` indicates how many results you are looking to retrieve. The `$after` parameter is used to retrieve additional pages and can be set to any object UUID. Typically, you'll retrieve the first page, and then set the `$after` parameter to the last object ID in the set of items that you retrieved.

> Please note that **the additional parameters are only available for some endpoints,** specifically those in our Graph API. Many endpoints, particularly assignment-related ones in the User API, will only respect the `$first` parameter. This is typically due to limitations within the APIs of the LMS systems we connect with.
> 
> **To achieve the best consistency across all endpoints, we recommend using the `$next` field as described above.** It works for all situations.

## Notes

* The `$cursor` provided in the `$next` field is time-sensitive. It will cease to work 2 hours after you receive it.
* The `$next` field is only provided if the request was successful.
