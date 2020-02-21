
```bash tab="Bash"
curl -X GET \
  https://pet-demo.machinable.io/api/dogs/5c869da3a7748bb224833f5c
```

```python tab="Python"
import requests

url = "https://pet-demo.machinable.io/api/dogs/5c869da3a7748bb224833f5c"

headers = {}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```javascript tab="javascript"
var data = null;

var xhr = new XMLHttpRequest();

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://pet-demo.machinable.io/api/dogs/5c869da3a7748bb224833f5c");

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

	url := "https://pet-demo.machinable.io/api/dogs/5c869da3a7748bb224833f5c"

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
  "_metadata": {
    "created": 1552326051,
    "creator": "anonymous",
    "creator_type": "anonymous"
  },
  "age": 7,
  "breed": "German Shephard",
  "id": "5c869da3a7748bb224833f5c",
  "name": "Max"
}

```
