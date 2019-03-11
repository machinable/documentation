
```bash tab="Bash"
curl -X GET \
  "https://pet-demo.machinable.io/collections/dogs?_limit=1&_offset=1"
```

```python tab="Python"
import requests

url = "https://pet-demo.machinable.io/collections/dogs?_limit=1&_offset=1"

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

xhr.open("GET", "https://pet-demo.machinable.io/collections/dogs?_limit=1&_offset=1");

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

	url := "https://pet-demo.machinable.io/collections/dogs?_limit=1&_offset=1"

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
        "created": 1552339933,
        "creator": "anonymous",
        "creator_type": "anonymous"
      },
      "age": 7,
      "breed": "German Shephard",
      "id": "5c86d3dda7748bb224833f68",
      "name": "Max"
    }
  ],
  "links": {
    "self": "http://pet-demo.machinable.io/collections/dogs?_limit=1&_offset=1",
    "prev": "http://pet-demo.machinable.io/collections/dogs?_limit=1&_offset=0"
  }
}
```
