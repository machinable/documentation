
Data stored in API Resource and Collection endpoints can be filtered, or searched, by adding a query parameter to the request URL with the field set to the value you want to search on.

!!! note "Limitations of Filtering"
    Data stored in Collections can only be filtered on **string data types**. If your application requires filtering on different data types, consider using API Resources as an alternative to Collections. Since API Resource data is defined with JSON Schema the type is known and, therefore, filterable.

    Filters can only currently support **exact matches**.

For example, if we want to search the `dogs` collection in the `Pet Demo` project for dogs that are of the breed "German Shephard", we would add the following to the request URL:

```bash
# filter
breed=German Shephard

# full URL
https://pet-demo.machinable.io/collections/dogs?breed=German%20Shephard
```

Using the URL above with the filter on `breed=German Shephard`, the full request and response will look like the following:

{!querying_data/queries/list.filter.md!}

The response `count` is the total count of results based on the filter.

Pagination will be based on the filter.

<br/>
