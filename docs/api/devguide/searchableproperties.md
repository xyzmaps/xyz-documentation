# Adjust Searchable Properties

> #### Note
>
>Your account needs access to the XYZ Maps Add-on Services.

This section describes how to use the extended capability of enabling property-search for
user-specified properties of your GeoJSON features inside a space.

It is recommended that you read the ["properties-search"](propertiessearch.md) guide before proceeding
with this more specific guide.

## Searching for features in a space

If the above prerequisites are fulfilled, adjusting the searchable properties can be done by
updating the space's `searchableProperties` property. This can be done using a `PATCH` request to
the `/spaces/{spaceId}` endpoint.

`searchableProperties` is a map of which the keys are property names and the values are boolean
flags telling whether the property should be searchable or not.

The following sample shows how to define `someProperty1` to be searchable and `someProperty2` to
be not searchable. In case you're wondering about the latter: This could be necessary to tell XYZ Maps
to revoke the decision of making `someProperty2` searchable in the automated algorithm.

**TL;DR**
*XYZ Maps has a space-specific algorithm to automatically decide which of the space's properties
are searchable. In case you desire other properties to be searchable the `searchableProperties` map
can be used to define that.*

```JSON
{
  "someProperty1": true,
  "someProperty2": false
}
```

Nested properties can be specified using the dot-notation e.g.:

```JSON
{
  "some.nested.property": true
}
```

It is also possible to define the datatype which is used on the property. Available datatypes
are object, array, string, number, and boolean. If the datatype is not given, an attempt is made 
to determine it automatically. The syntax is "someProperty::datatype"

```JSON
{
  "some.nested.property::array": true
}
```

*Remember: In a `PATCH`-operation only the properties to be changed are necessary*

### Request

*Try in [your local Swagger](http://localhost:8888/hub/static/swagger/#/Edit%20Spaces/patchSpace)*

```HTTP
PATCH /spaces/{spaceId}
```

with the following body

```JSON
{
    "searchableProperties": {
        "someProperty1": true,
        "someProperty2": false,
        "some.nested.property": true
    }
}
```

### Response

```JSON
{
    "title": "My Demo Space",
    "description": "Description as markdown",
    "searchableProperties": {
        "someProperty1": true,
        "someProperty2": false,
        "some.nested.property": true
    }
}
```
