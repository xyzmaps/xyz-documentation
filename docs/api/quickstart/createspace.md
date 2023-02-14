# Create a Space

See the following request and response for creating a new space:

## Request

*Try in [your local Swagger](http://localhost:8888/hub/static/swagger/#/Edit_Spaces)*

```HTTP
POST /spaces
```

with the following body:

```JSON
{
    "title": "My Demo Space",
    "description": "My Demo *Space* description"
}
```

> #### Info
>
> The Description can contain formatting in markdown format.

## Response

```JSON
{
    "id": "{spaceId}",
    "title": "My Demo Space",
    "description": "** My Demo *Space* description"
}
```

> #### Info
>
> The ID is a unique, randomly generated identifier and is mandatory as an argument in
> subsequent requests.
