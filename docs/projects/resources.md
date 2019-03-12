# API Resources

API Resources are endpoints which store JSON Objects that are described and validated by [JSON Schema](/documentation/reference/json_schema/). This gives you the ability to create API endpoints that will validate the data being saved to it without writing any code.

## Manage Resources

### Create a new API Resource

To create a new API Resource, navigate to your Project's `API` page and click the `New Resource` button. We will create a `Dogs` resource in our `Pet Demo` project.

![new resource](/images/new_resource.png "New API Resource")

Enter the following information into the `New Resource` fields:

**Title**
```
Dogs
```

**Path**
```
/dogs
```

**Properties**
```json
{
    "age": {
        "description": "Age, in human years, of the dog.",
        "type": "integer"
    },
    "breed": {
        "description": "The breed of the dog.",
        "type": "string"
    },
    "name": {
        "description": "The name of the dog.",
        "type": "string"
    }
}
```

Click `Save` to save the new `Dogs` API Resource. Once the Resource is created, you can immediately start [Creating and Querying data](/documentation/projects/resources/#querying-data)

### View Details

To view the details of an API Resource, click the ellipsis button and select `More`.

![details](/images/more.png "API Resource Details")


This will open a modal with the details of the selected API Resource:


![details](/images/view.png "API Resource Details")

**Settings**

Displays helpful information regarding the API Resource including the name, ID, and URL to the Resource's data. There are also a few editable fields here for `Parallel Read` and `Parallel Write` which control user access to the data. To learn more about these options, skip ahead to [Configure Access](/documentation/projects/resources/#configure-access)

**Properties**

This section shows the configured properties that describe the data for this API Resource. These are not editable.

**Data**

Lists the data stored within this API Resource as a paginated list that can be traversed.

### Configure Access

By default, [Project Users & API Keys](/documentation/projects/access/) with a "User" role will only have access to their data (i.e. objects that have been created by a User/API Key can only be accessed by that User/API Key). This is based on the Machinable managed `_metadata` object that is stored and returned within each object.

!!! note
    Users/API Keys with the role of "Admin" will have access to all API Resource data, based on that "User/API Key" access policy.

This access can be changed on a per API Resource basis by enabling the Parallel access fields:

**Parallel Read**

When enabled, any User/API Key can read (Get, List) any object, regardless of who/what created it. Disabled by default.

**Parallel Write**

When enabled, any User/API Key can write (Update, Delete) any object, regardless of who/what created it. Disabled by default.

## Querying Data

Refer to the [Querying](/documentation/querying_data/crud/) documentation to see detailed examples regarding how to query for API Resource and Collection data. The examples in the [Querying](/documentation/querying_data/crud/) documentation use a Collection but can be interchanged with the API Resource defined above.

### Possible Errors

{!querying_data/errors.md!}
