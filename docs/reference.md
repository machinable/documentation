# Reference

## JSON Schema

Machinable API Resource properties are defined with JSON Schema. This section provides helpful information and quick links on the topic of JSON Schema.

JSON Schema is a vocabulary that allows you to annotate and validate JSON documents. [Understanding JSON Schema](https://json-schema.org/understanding-json-schema/) is a great reference for those that want to understand the basics of JSON Schema, without diving into the technical specification.

For more information about the JSON Schema specification, refer to [https://json-schema.org](https://json-schema.org).

### Examples

These examples are meant to give you a high level idea of how to structure your data types in Machinable.

#### Person Schema

```json
{
    "firstName": {
        "type": "string",
        "description": "The person's first name."
    },
    "lastName": {
        "type": "string",
        "description": "The person's last name."
    },
    "age": {
        "description": "Age in years which must be equal to or greater than zero.",
        "type": "integer",
        "minimum": 0
    },
    "birthDate": {
        "description": "The date of this person's birth, represented by a RFC3339 formated date-time string",
        "format": "date-time",
        "type": "string"
    },
    "friends": {
        "description": "A list of this person's friends",
        "items": {
            "type": "string"
        },
        "type": "array"
    },
    "profession": {
        "description": "The profession of this person. What they do for a career or their lifestyle.",
        "type": "object",
        "properties": {
            "title": {
                "type": "string"
            },
            "years": {
                "type": "number",
                "description": "The number of years this person has spent with this profession"
            },
            "responsibilites": {
                "description": "A list of this profession's responsibilities",
                "items": {
                    "type": "string"
                },
                "type": "array"
            }
        }
    }
}
```

Person sample data:

```json
{
    "firstName": "Jonathan",
    "lastName": "Gilmore",
    "age": 29,
    "birthDate": "1989-07-20T04:00:00Z",
    "friends": [
        "Renee Scott",
        "Mrs. Brenda Harris",
        "Charles Miller",
        "Marc Webb"
    ],
    "profession": {
        "title": "Lumberjack",
        "years": 10.5,
        "responsibilites": [
            "North American workers in the logging industry who perform the initial harvesting and transport of trees for ultimate processing into forest products."
        ]
    }
}
```