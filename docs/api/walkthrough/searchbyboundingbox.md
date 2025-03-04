# Search by Bounding Box

> #### Note
>
> The endpoint for the API is <https://localhost:8080/hub>.

Searching by bounding box is searching a rectangle area of the map for features.

## Request

*Try in [your local Swagger](http://localhost:8888/hub/static/swagger/#/Read%20Spaces/getFeaturesByBBox)*

```HTTP
GET /spaces/{spaceId}/bbox?west=-110&north=53&east=-130&south=50&tags=
```

## Response

```JSON
{
  "type": "FeatureCollection",
  "features": [
    {
      "id": "{featureId}",
      "bbox": [
        -116.055555555,
        51.170833333,
        -116.055555555,
        51.170833333
      ],
      "type": "Feature",
      "properties": {
        "name": "Stanley Peak",
        "@ns:com:here:xyz": {
          "tags": [
            "canada",
            "mountain"
          ],
          "space": "{spaceId}",
          "createdAt": 1529855977981,
          "updatedAt": 1529855977981
        }
      },
      "geometry": {
        "type": "Point",
        "coordinates": [
          -116.055555555,
          51.170833333
        ]
      }
    },
    {
      "id": "{featureId}",
      "bbox": [
        -123.291,
        50.1203,
        -123.291,
        50.1203
      ],
      "type": "Feature",
      "properties": {
        "name": "Mount Cayley",
        "@ns:com:here:xyz": {
          "tags": [
            "canada",
            "mountain"
          ],
          "space": "{spaceId}",
          "createdAt": 1529855978027,
          "updatedAt": 1529855978027
        }
      },
      "geometry": {
        "type": "Point",
        "coordinates": [
          -123.291,
          50.1203
        ]
      }
    }
  ]
 }
```
