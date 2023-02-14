# Create a Space

> #### Note
>
> The endpoint for the API is <https://localhost:8080/hub>.

## Request

*Try in [your local Swagger](http://localhost:8888/hub/static/swagger/#/Edit%20Spaces/postSpace)*

```HTTP
POST /spaces
```

```JSON
{

    "title": "My Demo Space",
    "description": "Description as markdown"

}
```

## Response

```JSON
{
    "id": "x-demospace",
    "owner":"{appId}",
    "title": "My Demo Space",
    "description": "Description as markdown"
}
```
