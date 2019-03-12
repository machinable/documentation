
```bash tab="Bash"
curl -X PUT \
  https://pet-demo.machinable.io/collections/dogs/5c869da3a7748bb224833f5c \
  -d '{
        "age": 9,
        "name": "Maximilian"
    }'
```

```python tab="Python"
import requests

url = "https://pet-demo.machinable.io/collections/dogs/5c869da3a7748bb224833f5c"

payload = "{\n    \"age\": 9,\n    \"name\": \"Maximilian\"\n}"
headers = {}

response = requests.request("PUT", url, data=payload, headers=headers)

print(response.text)
```

```javascript tab="javascript"
var data = "{\n    \"age\": 9,\n    \"name\": \"Maximilian\"\n}";

var xhr = new XMLHttpRequest();

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("PUT", "https://pet-demo.machinable.io/collections/dogs/5c869da3a7748bb224833f5c");

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

	url := "https://pet-demo.machinable.io/collections/dogs/5c869da3a7748bb224833f5c"

	payload := strings.NewReader("{\n    \"age\": 9,\n    \"name\": \"Maximilian\"\n}")

	req, _ := http.NewRequest("PUT", url, payload)

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
    "age": 9,
    "breed": "German Shephard",
    "id": "5c869da3a7748bb224833f5c",
    "name": "Maximilian"
}
```
