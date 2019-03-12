
API Resources and Collections may return the following error status codes.

|Status Code|Description|
|-----------|-----------|
|`400 Bad Request`|A field is missing or is of the wrong data type based on the JSON Schema for the Resource|
|`401 Unauthorized`|Missing or invalid authorization header|
|`403 Forbidden`|The requester is not allowed to access the resource|
|`404 Not Found`|The resource or object does not exist|
|`500 Internal Server Error`|An unknown error occurred, try again later|