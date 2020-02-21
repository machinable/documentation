
```bash tab="Bash"
curl -X DELETE \
  https://pet-demo.machinable.io/api/dogs/5c869da3a7748bb224833f5c
```

```python tab="Python"
import requests

url = "https://pet-demo.machinable.io/api/dogs/5c869da3a7748bb224833f5c"

headers = {}

response = requests.request("DELETE", url, headers=headers)

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

xhr.open("DELETE", "https://pet-demo.machinable.io/api/dogs/5c869da3a7748bb224833f5c");

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

	req, _ := http.NewRequest("DELETE", url, nil)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

Successful response:
```json
< HTTP/1.1 204 No Content
```
