
```bash tab="Bash"
curl -X GET \
  "https://pet-demo.machinable.io/collections/dogs?breed=German%20Shephard"
```

```python tab="Python"
import requests

url = "https://pet-demo.machinable.io/collections/dogs?breed=German%20Shephard"

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

xhr.open("GET", "https://pet-demo.machinable.io/collections/dogs?breed=German%20Shephard");

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

	url := "https://pet-demo.machinable.io/collections/dogs?breed=German%20Shephard"

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
    "count": 1,
    "items": [
        {
            "_metadata": {
                "created": 1552333754,
                "creator": "anonymous",
                "creator_type": "anonymous"
            },
            "age": 9,
            "breed": "German Shephard",
            "id": "5c86d3dda7748bb224833f68",
            "name": "Maximilian"
        }
    ],
    "links": {
        "self": "https://pet-demo.machinable.io/collections/dogs?_limit=10&_offset=0&breed=German Shephard"
    }
}
```
