# Access

Project Access provides tools to create and manage Project Users and API Keys. These two entities are how someone or something interacts with the Project data stored in API Resources and Collections.

!!! note
    If your project authentication is disabled, anyone can access API Resource and Collection data for the project. Project Users and API Keys are note necesseary in this case.

## Users

Project Users are intended to be end users of your Machinable Project. They are able to acquire a session and interact with the Project Data based on access policies. 

### Create User

To create a new Project User navigate to your Project's `Access > Users` page.

![empty users](../images/empty_users.png "No Users")

Click the `Create A User` button to open the new user modal and enter the new user's information.

![new users](../images/create_user.png "New User")

**Username**

This user's username, used to login and obtain a session.

**Password**

This user's password, used to login and obtain a session. This should be recorded and kept secret, you will not be able to retrieve the password.

**Role & Access**

The User's Role controls what objects they are able to access. `Users` will only have access to objects that they have created, depending on the Resource/Collection access policy. `Administrators` will have access to all created objects.

The User's Access will determine how they can interact with the data. `Read` will allow the User to Get and List objects. `Write` will allow the User to Create, Edit, and Delete objects.

### Edit User

To edit a User's Role & Access, click the ellipsis button for that user and select `Edit Access`.

![edit users](../images/edit_user.png "Edit User")

### Authentication

In order to make authenticated requests to API Resources and Collections, Project Users will need an access token.

First, the user will need to obtain a session. To do that, make an [HTTP Basic authentication](https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication#Basic_authentication_scheme) request to your project's `/sessions` endpoint. This will return an `access_token` and a `refresh_token` in the form of [JSON Web Tokens](https://jwt.io/):

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

Access tokens have a limited lifetime of 5 minutes. They then need to be exchanged for a new Access token using the refresh token returned in the `/sessions/` response.

### Refresh Tokens

After the access token has expired, client requests will return with a `401 Unauthorized` status code. When this happens, the client can attempt to "refresh" their existing session by exchanging the refresh token for a new access token. This is done by making a `POST` to the project's `/sessions/refresh` endpoint with the header `Authorization: Bearer {refresh_token}`. Refer to the example request below to see how the refresh token is used to get a new access token:

{!querying_data/queries/refresh.md!}

The client can then use this new access token to make requests.

!!! note
    Refresh tokens also expire after a certain amount of time.

If the refresh request returns `401 Unauthorized` then the refresh token is expired as well and the user will need to obtain a new session by logging in again.

## API Keys

Project API Keys are intended to be used by other software/machines. They can be useful if you want to proxy user requests, automatically manage data, or run tests against Machinable.

### Create API Key

To create a new Project API Key navigate to your Project's `Access > API Keys` page.

![empty api keys](../images/empty_keys.png "No API Keys")

Click the `Generate API Token` button to open the new API Key modal and enter the API Key's information.

![new api keys](../images/new_apikey.png "New API Key")

**Generated Key**

This is the automatically generated API Key. Be sure to copy the API Key and save it somewhere safe as you will not be able to view it again.

**Description**

The description is meant to help you identify the API Key being used by your client and Machinable logs.

**Role & Access**

This is identical to the Project User Role & Access.

The API Key's Role controls what objects it is able to access. `Users` will only have access to objects that they have created, depending on the Resource/Collection access policy. `Administrators` will have access to all created objects.

The API Key's Access will determine how it can interact with the data. `Read` will allow the API Key to Get and List objects. `Write` will allow the API Key to Create, Edit, and Delete objects.

### Edit API Key

To edit an API Key's Role & Access, click the ellipsis button for that API Key and select `Edit Access`.

![edit api keys](../images/edit_apikey.png "Edit API Key")

### Authentication

To make authenticated requests with a Project API Key, add the `Authorization` header with the `apikey` text to each request:

```bash
Authorization: apikey {api_key_string}
```

<br/>
