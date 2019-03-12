```bash tab="Bash"
curl -X POST \
  https://pet-demo.machinable.io/sessions/refresh/ \
  -H 'authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE1NTI1ODExMTksInNlc3Npb25faWQiOiI1Yzg2OGQ3ZmE3NzQ4YmIyMjQ4MzNmNGMiLCJ1c2VyX2lkIjoiNWM4NjhkNDBhNzc0OGJiMjI0ODMzZjRiIn0.wWyb-nNff3RBw73D1hqN9k8U8_pKMHWGShMwA9YvSAc'
```

```python tab="Python"
import requests

url = "https://pet-demo.machinable.io/sessions/refresh/"

headers = {
    'authorization': "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE1NTI1ODExMTksInNlc3Npb25faWQiOiI1Yzg2OGQ3ZmE3NzQ4YmIyMjQ4MzNmNGMiLCJ1c2VyX2lkIjoiNWM4NjhkNDBhNzc0OGJiMjI0ODMzZjRiIn0.wWyb-nNff3RBw73D1hqN9k8U8_pKMHWGShMwA9YvSAc"
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

xhr.open("POST", "https://pet-demo.machinable.io/sessions/refresh/");
xhr.setRequestHeader("authorization", "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE1NTI1ODExMTksInNlc3Npb25faWQiOiI1Yzg2OGQ3ZmE3NzQ4YmIyMjQ4MzNmNGMiLCJ1c2VyX2lkIjoiNWM4NjhkNDBhNzc0OGJiMjI0ODMzZjRiIn0.wWyb-nNff3RBw73D1hqN9k8U8_pKMHWGShMwA9YvSAc");

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

	url := "https://pet-demo.machinable.io/sessions/refresh/"

	req, _ := http.NewRequest("POST", url, nil)

	req.Header.Add("authorization", "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE1NTI1ODExMTksInNlc3Npb25faWQiOiI1Yzg2OGQ3ZmE3NzQ4YmIyMjQ4MzNmNGMiLCJ1c2VyX2lkIjoiNWM4NjhkNDBhNzc0OGJiMjI0ODMzZjRiIn0.wWyb-nNff3RBw73D1hqN9k8U8_pKMHWGShMwA9YvSAc")

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
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE1NTIzMjI4MTksInByb2plY3RzIjp7InBldC1kZW1vIjp0cnVlfSwidXNlciI6eyJhY3RpdmUiOnRydWUsImlkIjoiNWM4NjhkNDBhNzc0OGJiMjI0ODMzZjRiIiwibmFtZSI6InRlc3RVc2VyIiwicmVhZCI6dHJ1ZSwidHlwZSI6InByb2plY3QiLCJ3cml0ZSI6dHJ1ZX19.93H4H3FyPGrzOGb3WHRO7RLUGezpYxbVki7oGqdyA6E"
}
```
