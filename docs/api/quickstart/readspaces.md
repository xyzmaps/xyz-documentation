# Read Spaces

Once you have acquired your credentials, you can determine the spaces to which you have access.

## Request

*Try in [your local Swagger](http://localhost:8888/hub/static/swagger/#/Read_Spaces)*

```HTTP
GET /spaces
```

## Response

```JSON
[
    {
        "id": "x-demospace",
        "title": "My Demo Space",
        "description": "Description as markdown"
    }
]
```
