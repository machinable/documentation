
```bash tab="Bash"
curl -X GET \
  "https://pet-demo.machinable.io/api/dogs?_limit=1"
```

```python tab="Python"
import requests

url = "https://pet-demo.machinable.io/api/dogs?_limit=1"

headers = {}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```javascript tab="Javascript"
var data = null;

var xhr = new XMLHttpRequest();

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://pet-demo.machinable.io/api/dogs?_limit=1");

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

	url := "https://pet-demo.machinable.io/api/dogs?_limit=1"

	req, _ := http.NewRequest("GET", url, nil)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))
}
```

Successful response:
```json
< HTTP/1.1 200 OK

{
  "count": 2,
  "items": [
    {
      "_metadata": {
        "created": 1552323811,
        "creator": "anonymous",
        "creator_type": "anonymous"
      },
      "age": 2,
      "breed": "French Bulldog",
      "id": "5c8694e3a7748bb224833f51",
      "name": "Murphy"
    }
  ],
  "links": {
    "self": "https://pet-demo.machinable.io/api/dogs?_limit=1&_offset=0",
    "next": "https://pet-demo.machinable.io/api/dogs?_limit=1&_offset=1"
  }
}
```
