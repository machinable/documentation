
```bash tab="Bash"
$ curl -X POST \
  https://pet-demo.machinable.io/api/dogs \
  -d '{"name":"Murphy", "age":2, "breed": "French Bulldog"}'
```

```python tab="Python"
import requests

url = "https://pet-demo.machinable.io/api/dogs"

payload = "{\"name\":\"Murphy\", \"age\":2, \"breed\": \"French Bulldog\"}"
headers = {}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```javascript tab="Javascript"
var data = "{\"name\":\"Murphy\", \"age\":2, \"breed\": \"French Bulldog\"}";

var xhr = new XMLHttpRequest();

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://pet-demo.machinable.io/api/dogs");

xhr.send(data);
```

```go tab="Go"
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://pet-demo.machinable.io/api/dogs"

	payload := strings.NewReader("{\"name\":\"Murphy\", \"age\":2, \"breed\": \"French Bulldog\"}")

	req, _ := http.NewRequest("POST", url, payload)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

Successful response:
```json
< HTTP/1.1 201 Created

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
```
