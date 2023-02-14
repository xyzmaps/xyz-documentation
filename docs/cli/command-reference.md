# XYZ Maps CLI Command Reference

In this section you can find all the supported commands and subcommands along with supported options.

## here

```console
Commands:
  xyz|xs [list|create|upload]             work with XYZ Maps spaces
  transform|tf [csv2geo|shp2geo|gpx2geo]  convert from csv/shapefile/gpx to geojson
  help [command]                          display help for command
```


### [xyz](basic-features.md#interact-with-data-hub-spaces)

XYZ Maps Space related operations

```console
Commands:
  list|ls [options]        information about available XYZ Maps Spaces
  analyze [options] <id>   property based analysis of the content of the
                           given [id]
  hexbin [options] <id>    create fixed height hexbins (and their centroids)
                           using points in a XYZ Maps space, and upload them to
                           another space
  show [options] <id>      shows the content of the given [id]
  delete [options] <id>    delete the XYZ Maps Space with the given id
  create [options]         create a new XYZ Maps Space
  clear [options] <id>     clear data from XYZ Maps Space
  token [options]          list all XYZ Maps tokens
  upload [options] [id]    upload GeoJSON, CSV, or a Shapefile to the given
                           id -- if no spaceID is given, a new Space will be
                           created
  config [options] [id]    configure/view advanced XYZ Maps features for
                           space
  join [options] <id>      {XYZ Maps Add-on} create a new virtual XYZ Maps
                           space with a CSV and a Space with geometries,
                           associating by feature ID
  virtualize|vs [options]  {XYZ Maps Add-on} create a new virtual XYZ Maps
                           space
  gis [options] <id>       {XYZ Maps Add-on} perform gis operations with
                           Space data
  help [command]           display help for command
```

#### [create](basic-features.md#create-a-new-space)

Create a new XYZ Maps Space.

```console
Options:
  -t, --title [title]       Title for Space
  -d, --message [message]   Short description
  -s, --schema [schemadef]  set json schema definition (local filepath / http
                            link) for your Space, all future data for this
                            Space will be validated for the schema
  -h, --help                display help for command
```

#### [list](basic-features.md#list-spaces)

Information about available XYZ Maps spaces

```console
Options:
  -r, --raw          show raw Space definition
  --filter <filter>  a comma separted strings to filter Spaces
  -p, --prop <prop>  property fields to include in table (default: [])
  -h, --help         display help for command
```

#### [show](basic-features.md#show-contents-of-a-space)

Shows the contents of the given XYZ Maps Space.

```console
Options:
  -l, --limit <limit>        Number of objects to be fetched
  -o, --offset <offset>      The offset / handle to continue the iteration
  -t, --tags <tags>          Tags to filter on
  -r, --raw                  show raw Space content
  --all                      iterate over entire Space to get entire
                             data of space, output will be shown on the console
                             in geojson format
  --geojsonl                 to print output of --all in geojsonl format
  -c, --chunk [chunk]        chunk size to use in --all option, default 5000
  -p, --prop <prop>          selection of properties, use p.<FEATUREPROP> or
                             f.<id/updatedAt/tags/createdAt>
  -w, --web                  display Space on xyzmaps.github.io/geojson-tool/
  -v, --vector               inspect and analyze using XYZ Maps Space Invader
                             on xyzmaps.github.io/xyz-space-invader
  -x, --permanent            generate a permanent token for --web and --vector option
  -s, --search <propfilter>  search expression in "double quotes", use single
                             quote to signify string value,  use
                             p.<FEATUREPROP> or f.<id/updatedAt/tags/createdAt>
                             (Use '+' for AND , Operators : >,<,<=,<=,=,!=)
                             (use comma separated values to search multiple
                             values of a property) {e.g.,
                             "p.name=John,Tom+p.age<50+p.phone='9999999'+p.zipcode=123456"}
  --spatial                  indicate to make spatial search on the space
  --radius <radius>          make a radius spatial search using --center, 
                             or thicken an input line or polygon (in meters)
  --center <center>          comma separated, double quoted lon,lat values to specify the
                             center point for radius search
  --feature <feature>        comma separated spaceid,featureid values to
                             specify reference geometry (taken from feature)
                             for spatial query
  --geometry <geometry>      geometry file to upload for spatial query (single
                             feature in geojson file)
  -h, --help                 display help for command
```

#### [upload](basic-features.md#uploadupdate-data-to-a-space)

Upload GeoJSON, CSV, or a Shapefile to the given Space -- if no spaceID is given, a new space will be created. GeoJSON feature IDs will be respected unless you override with -o or specify with -i; pipe GeoJSON via stdout using | xyzmaps space upload spaceid

```console
  -f, --file <file>               comma separated list of local GeoJSON,
                                  GeoJSONL, Shapefile, CSV, GPX, or XLS/X files (or
                                  GeoJSON/CSV URLs); use a directory path and
                                  --batch [filetype] to upload all files of
                                  that type within a directory
  -c, --chunk [chunk]             chunk size, default 200 -- use smaller values
                                  (1 to 10) to allow safer uploads of very
                                  large geometries (big polygons, many
                                  properties), use higher values (e.g., 500 to
                                  5000) for faster uploads of small geometries
                                  (points and lines, few properties)
  -t, --tags [tags]               fixed tags for features uploaded to the XYZ Maps space
  --token <token>                 a external token to upload data to another
                                  user's Space
  -x, --lon [lon]                 longitude field name
  -y, --lat [lat]                 latitude field name
  -z, --point [point]             points field name with coordinates like
                                  (Latitude,Longitude) e.g., (37.7,-122.4)
  --lonlat                        parse a -—point/-z csv field as (lon,lat)
                                  instead of (lat,lon)
  -p, --ptag [ptag]               property name(s) to be used to add tags,
                                  property_name@value, best for a small number of
                                  quantitative values
  -i, --id [id]                   property name(s) to be used as the feature ID
                                  (must be unique) -- multiple values can be
                                  comma separated
  -a, --assign                    interactive mode to analyze and select fields
                                  to be used as tags and unique feature IDs
  -o, --override                  override existing GeoJSON feature ID and 
                                  generate property hash as feature ID
  -s, --stream                    streaming support for upload  and/or large
                                  csv and geojson uploads using concurrent
                                  writes, tune chunk size with -c
  -d, --delimiter [,]             alternate delimiter used in CSV (default:
                                  ",")
  -q, --quote ["]                 quote used in CSV (default: "\"")
  -e, --errors                    print data upload errors
  --string-fields <stringFields>  property name(s) of CSV string fields *not*
                                  to be automatically converted into numbers or
                                  booleans (e.g., number-like census geoids,
                                  postal codes with leading zeros)
  --groupby <groupby>             consolidate multiple rows of a CSV into a
                                  single feature based on a unique ID
                                  designated with -i; values of each row within
                                  the selected column will become top level
                                  properties within the consolidated feature
  --promote <promote>             comma separated column names which should not be nested within a top level property generated consolidated by --groupby
  --flatten                       stores the --groupby consolidated output in flattened string separated by colon (:) instead of a nested object
  --date <date>                   date-related property name(s) of a feature to
                                  be normalized as a ISO 8601 datestring
                                  (datahub_iso8601_[propertyname]), and unix
                                  timestamp (datahub_timestamp_[propertyname]
  --datetag [datetagString]       comma separated list of granular date tags to
                                  be added via --date. possible options - year,
                                  month, week, weekday, year_month, year_week,
                                  hour
  --dateprops [datepropsString]   comma separated list of granular date
                                  properties to be added via --date. possible
                                  options - year, month, week, weekday,
                                  year_month, year_week, hour
  --noCoords                      upload CSV files with no coordinates,
                                  generates null geometry (best used with -i
                                  and virtual spaces)
  --history [history]             repeat commands previously used to upload
                                  data to a space; save and recall a specific
                                  command using "--history save" and "--history
                                  fav"
  --batch [batch]                 upload all files of the same type within a
                                  directory; specify "--batch
                                  [geojson|geojsonl|csv|shp|gpx]" (will inspect
                                  shapefile subdirectories). select directory
                                  with -f
  -h, --help                      display help for command
```

#### [clear](basic-features.md#clear-a-space)

Clear data from a XYZ Maps Space.

```console
Options:
  -t, --tags <tags>  tags for the Space
  -i, --ids <ids>    ids for the Space
  --force            skip the confirmation prompt
  -h, --help         display help for command
```

#### [delete](basic-features.md#delete-a-space)

Delete a given Space.

```console
Options:
  --force          skip the confirmation prompt
  -h, --help       display help for command
```

#### [token](basic-features.md#list-all-tokens)

List all XYZ Maps tokens.

```console
Options:
  --console   opens web console for XYZ Maps
  -h, --help  display help for command
```

#### [config](basic-features.md#get-or-update-more-information-about-your-spaces)

Configure/view advanced XYZ Maps features for a Space.

```console
Options:
  --shared <flag>             set your space as shared / public (default is
                              false)
  --readonly <flag>.          set your space as readOnly (default is false)
  -t,--title [title]          set title for the Space
  -d,--message [message]      set description for the Space
  -c,--copyright [copyright]  set copyright text for the Space
  --cacheTTL <cacheTTL>       set cacheTTL value for the Space with valid
                              number
  --stats                     see detailed space statistics
  -r, --raw                   show raw json output
  -s,--schema [schemadef]     view or set schema definition (local filepath /
                              http link) for your Space, applicable on future
                              data, use with add/delete/update
  --searchable                view or configure searchable properties of a
                              Space, use with add/delete/update
  --tagrules                  add, remove, view the conditional rules to tag
                              your features automatically, use with
                              add/delete/update -- at present all tag rules
                              will be applied synchronously before features are
                              stored ( mode : sync )
  --delete                    use with schema/searchable/tagrules options to
                              remove the respective configurations
  --add                       use with schema/searchable/tagrules options to
                              add/set the respective configurations
  --update                    use with tagrules options to update the
                              respective configurations
  --view                      use with schema/searchable/tagrules options to
                              view the respective configurations
  --activitylog               configure activity logs for your Space
                              interactively
  --console                   opens web console for XYZ Maps
  -h, --help                  display help for command
```

#### [virtualize](add-on.md#virtual-spaces)

Create a new virtual Space.

```cli
Options:
  -t, --title [title]         Title for virtual Space
  -d, --message [message]     set description for the Space
  -g, --group [spaceids]      Group the Spaces (all objects of each space will
                              be part of the response) - enter comma separated
                              Space ids
  -a, --associate [spaceids]  Associate the Spaces. Features with same id will
                              be merged into one feature. Enter comma separated
                              space ids [space1,space2] -- space1 properties
                              will be merged into space2 features.
  -h, --help                  display help for command
```

#### [join](add-on.md#join-virtual-spaces)

Create a new virtual Space with a CSV and a space with geometries, associating by feature ID.

```console
Options:
  -f, --file <file>               csv to be uploaded and associated
  -i, --keyField <keyField>       field in csv file to become feature id
  -x, --lon [lon]                 longitude field name
  -y, --lat [lat]                 latitude field name
  -z, --point [point]             points field name with coordinates like
                                  (Latitude,Longitude) e.g., (37.7,-122.4)
  --lonlat                        parse a —point/-z csv field as (lon,lat)
                                  instead of (lat,lon)
  -d, --delimiter [,]             alternate delimiter used in csv (default:
                                  ",")
  -q, --quote ["]                 quote used in csv (default: "\"")
  --token <token>                 a external token to create another user's
                                  Spaces
  -s, --stream                    streaming data for faster uploads and large
                                  csv support
  --string-fields <stringFields>  property name(s) of CSV string fields *not*
                                  to be automatically converted into numbers or
                                  booleans (e.g., number-like census geoids,
                                  postal codes with leading zeros)
  --groupby <groupby>             consolidate multiple rows of a CSV into a
                                  single feature based on a unique ID
                                  designated with -i; values of each row within
                                  the selected column will become top level
                                  properties within the consolidated feature
  -h, --help                      display help for command
```

#### [hexbin](add-on.md#hexbin)

Create fixed height hexbins (and their centroids) using points in a Space, and upload them to another Space.

```console
Options:
  -c, --cellsize <cellsize>      size of hexgrid cells in meters,
                                 comma-separate multiple values
  -i, --ids                      add IDs of features counted within the hexbin
                                 as an array in the hexbin's feature property
  -p, --groupBy <groupBy>        name of the feature property by which hexbin
                                 counts will be further grouped
  -a, --aggregate <aggregate>    name of the feature property used for
                                 aggregating sum value of all the features
                                 inside a hexbin
  -r, --readToken <readToken>    token of another user's source space, from
                                 which points will be read
  -w, --writeToken <writeToken>  token of another user's target space to which
                                 hexbins will be written
  -t, --tags <tags>              only make hexbins for features in the source
                                 space that match the specific tag(s),
                                 comma-separate multiple values
  -b, --bbox [bbox]              only create hexbins for records inside the
                                 bounding box specified either by individual
                                 coordinates provided interactively or as
                                 minLon,minLat,maxLon,maxLat (use “\ “ to
                                 escape a bbox with negative coordinate(s))
  -l, --latitude <latitude>      latitude which will be used for converting
                                 cellSize from meters to degrees
  -z, --zoomLevels <zoomLevels>  hexbins optimized for zoom levels (1-18) -
                                 comma separate multiple values(-z 8,10,12) or
                                 dash for continuous range(-z 10-15)
  -h, --help                     display help for command
```

#### [gis](add-on.md#gis)

Perform GIS operations with space data.

```console
Options:
  --centroid             calculates centroids of Line and Polygon features and
                         uploads in a different Space
  --length               calculates length of LineString features and adds new properties
  --area                 calculates area of Polygon features and adds new properties
  --voronoi              calculates Voronoi Polygons of point features and
                         uploads in different Space
  --tin                  calculates Delaunay Polygons of point features and
                         uploads in different Space
  --property <property>  populates Delaunay polygons' properties based on the
                         specified feature property
  -c, --chunk [chunk]    chunk size, default 20 -- default for polygons,
                         increase for faster point feature uploads
  -t, --tags <tags>      source Space tags to filter on
  --samespace            option to upload centroids/voronoi/tin to same Space,
                         use tags to filter
  -h, --help             display help for command
```

### transform

Transform various file formats to geojson.

```console
Commands:
  csv2geo [options] <path>  convert csv to geojson
  shp2geo <path>            convert shapefile to geojson
  gpx2geo <path>            convert gpx to geojson
  help [command]            display help for command
```

#### csv2geo

Convert a csv file to geojson.

```console
Options:
  -y, --lat [lat]                 latitude field name
  -x, --lon [lon]                 longitude field name
  -d, --delimiter [,]             delimiter used in csv (default: ",")
  -q, --quote ["]                 quote used in csv (default: "\"")
  -z, --point [point]             points field name
  --string-fields <stringFields>  comma seperated property names which needs to
                                  be converted as String even though they are
                                  numbers or boolean e.g. postal code
  -h, --help                      display help for command
```
