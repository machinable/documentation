When making calls to Machinable API Resources or Collections, there may be a ton of results to return, depending on your use case. In order to keep response sizes small and more manageable, results are returned as a paginated list.

Take a look at the response of the following list operation to the `dogs` Collection in our `Pet Demo` project:

{!querying_data/queries/list.md!}

As you can see, there are **3** keys at the root of the JSON response; `count`, `links`, and `items`.

**count** is the total count of results for the query. Based on our request, we now know there are a total of 2 dogs in the `dogs` collection because we are not filtering the data in any way.

**links** provides context to what URLs we can request to traverse forward or backward through the paginated results.

**items** contains each object returned _for the page we are requesting_. The page we are requesting is determined by the query parameters `_limit` and `_offset`.

### Limit

`_limit` is a query parameter that can be used to specify how many results you would like to see in a single response payload. If we take a look at our sample request above, we'll see that we are not specifying a limit, so Machinable will default the page size to 10.

If we specify `_limit` of `1`, we will only get the first result of the `dogs` objects:

{!querying_data/queries/list.1.md!}

!!! info
    The `_limit` query parameter is a reserved field that cannot be used in API Resource or Collection data fields.

    The `_limit` query parameter has the following constraints:

    Maximum: 100 <br/>
    Minimum: 1 <br/>
    Default: 10 <br/>

### Offset

`_offset` is a query parameter that can be used to specify how many results to skip before the response payload is built and returned. If we take a look at our sample request above, we'll see that we are not specifying an offset, so Machinable will default the offset to 0, giving us the first page of the results.

If we continue to build off of the request in our example and provide an `_offset` of `1` with a `_limit` of `1`, we will get the second "page" of results. Since there are only `2` dogs in the collection, the second page will be the last page:

{!querying_data/queries/list.2.md!}

!!! info
    The `_offset` query parameter is a reserved field that cannot be used in API Resource or Collection data fields.

    The `_offset` query parameter has the following constraints:

    Minimum: 0 <br/>
    Default: 0 <br/>


With the use of `_limit` and `_offset` we can _traverse_ the entire list of results without having to return all of them in a single request.

### Links

The `links` field provides contextual URLs for the current (`self`), `next`, and `prev` (previous) page of results. This can be helpful when creating a paginated table of data so the table does not have to keep track of which page it is on (limit and offset), only what the `next` and `prev` URLs are, which will be returned with each list request.

<br/>