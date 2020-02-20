```sh
curl -s -X POST -d '{"name": "Lucy", "breed": "mut", "age": 5}' -H "Authorization: apikey $API_KEY" https://pet-demo.machinable.io/api/dogs | jq "."
{
  "_metadata": {
    "creator": "186f5d7a-58bf-47cd-ae29-cf4137bd8bc9",
    "creator_type": "apikey",
    "created": 1582234699
  },
  "age": 5,
  "breed": "mut",
  "id": "b9737cfa-a69e-44e9-8f52-5bb1bed1f5ae",
  "name": "Lucy"
}
```

hook result
```json
{
  "entity_key": "dogs",
  "entity_type": "resource",
  "event": "create",
  "payload": {
    "_metadata": {
      "created": 1582234699,
      "creator": "186f5d7a-58bf-47cd-ae29-cf4137bd8bc9",
      "creator_type": "apikey"
    },
    "age": 5,
    "breed": "mut",
    "id": "b9737cfa-a69e-44e9-8f52-5bb1bed1f5ae",
    "name": "Lucy"
  },
  "project_Id": "02327c9f-b523-45b6-b8a1-4cd47565aeba"
}
```