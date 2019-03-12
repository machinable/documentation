Machinable's main feature is the ability to perform CRUD (Create, Read, Update, Delete) operations on your project's API Resource and Collection endpoints.

API Resources and Collections use the same syntax when performing CRUD operations. The only difference between the two is API Resources will return `400 Bad Request` when creating an object that does not match the defined JSON Schema. 


!!! note
    See [API Resources](/documentation/projects/resources/) for more information about data validation with JSON Schema.

All examples will be using the `Pet Demo` project, which has the following project URL:

```
https://pet-demo.machinable.io
```

## Authentication

!!! note
    If your project authentication policy is disabled, you do not need to provide an Authorization header in your requests. **The examples on this page do not make use of an Authorization header.**

Depending on how you are accessing your project's data, you may need to authenticate your requests.

### API Keys

To make authenticated requests with an [API Key](/documentation/projects/access/#api-keys), add the `Authorization` header with the `apikey` text to each request:

```bash
Authorization: apikey {api_key_string}
```

### Users

User authenticated requests require a bit more work.

First, the user will need to acquire a session. To do that, make an [HTTP Basic authentication](https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication#Basic_authentication_scheme) request to your project's `/sessions` endpoint. This will return an `access_token` and a `refresh_token` in the form of [JSON Web Tokens](https://jwt.io/):

```bash tab="Bash"
# base64 encode username|password to make HTTP Basic authn request
$ echo "testUser:hunter2" | base64
dGVzdFVzZXI6aHVudGVyMgo=

# POST credentials to /sessions/ endpoint to recieve access token
$ curl -X POST \
  https://pet-demo.machinable.io/sessions/ \
  -H 'authorization: Basic dGVzdFVzZXI6aHVudGVyMg=='
```

```python tab="Python"
import requests

url = "https://pet-demo.machinable.io/sessions/"

headers = {
    'authorization': "Basic dGVzdFVzZXI6aHVudGVyMg=="
    }

response = requests.request("POST", url, headers=headers)

print(response.text)
```

```javascript tab="Javascript"
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://pet-demo.machinable.io/sessions/");
xhr.setRequestHeader("authorization", "Basic dGVzdFVzZXI6aHVudGVyMg==");

xhr.send(data);
```

```go tab="Go"
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://pet-demo.machinable.io/sessions/"

	req, _ := http.NewRequest("POST", url, nil)
 
	req.Header.Add("authorization", "Basic dGVzdFVzZXI6aHVudGVyMg==")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

Successful response:
```json
{
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE1NTIzMjI4MTksInByb2plY3RzIjp7InBldC1kZW1vIjp0cnVlfSwidXNlciI6eyJhY3RpdmUiOnRydWUsImlkIjoiNWM4NjhkNDBhNzc0OGJiMjI0ODMzZjRiIiwibmFtZSI6InRlc3RVc2VyIiwicmVhZCI6dHJ1ZSwidHlwZSI6InByb2plY3QiLCJ3cml0ZSI6dHJ1ZX19.93H4H3FyPGrzOGb3WHRO7RLUGezpYxbVki7oGqdyA6E",
  "message": "Successfully logged in",
  "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE1NTI1ODExMTksInNlc3Npb25faWQiOiI1Yzg2OGQ3ZmE3NzQ4YmIyMjQ4MzNmNGMiLCJ1c2VyX2lkIjoiNWM4NjhkNDBhNzc0OGJiMjI0ODMzZjRiIn0.wWyb-nNff3RBw73D1hqN9k8U8_pKMHWGShMwA9YvSAc",
  "session_id": "5c868d7fa7748bb224833f4c"
}
```

Once the user has a session, authenticated requests can be made by adding the `Authorization` header with the `bearer` text and `access_token` to each request:

```bash
Authorization: bearer {access_token}
```

!!! info
    Access tokens have a limited lifetime of 5 minutes. They then need to be exchanged for a new Access token using the refresh token. Refer to [Project Users](/documentation/projects/access/#refresh-tokens) for more information about refreshing an access token.

## Create

Create and store a new object in a specific Collection or API Resource.

!!! note
    These examples are managing data within a **Collection** called `dogs` (`/collections/dogs`). These requests could also manage data within an **API Resource** called `dogs` at `/api/dogs`, given the correct JSON schema is defined.

{!querying_data/queries/create.md!}

## Read

Retrieve a single object from a collection or list all objects that exist (paginated).

### Retrieve single object

To retrieve a single object, make a `GET` request to the collection with the ID of the object as the last path parameter.

{!querying_data/queries/get.md!}

### List objects

To retrieve a paginated list of objects for this collection, make a `GET` request to the collection.

{!querying_data/queries/list.md!}

Notice the collection objects are returned as a list in the `items` key. A maximum of 10 objects will be returned by default. 

See [Pagination](/documentation/querying_data/pagination) for more information regarding the page limit as well as the other keys in the root of the response JSON.

## Update

Update a single object's values.

{!querying_data/queries/update.md!}

## Delete

Permanently remove an object.

{!querying_data/queries/delete.md!}

<br/>