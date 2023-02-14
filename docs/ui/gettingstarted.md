# Getting Started with XYZ Maps UI

Even when you're using a Playground sample as a starting point, it's good to know the mechanics of the
data ends up on the map. And when you're starting from scratch, it's vital that you understand how to
make all of it happen yourself.

## Setup Basic Map Display

1. Create a basic HTML and load the modules

    ```html
    <!DOCTYPE html>
      <html>
        <head>
          <script src="https://localhost:8080/maps/latest/xyz-maps-common.min.js" type="text/javascript" charset="UTF-8" ></script>
          <script src="https://localhost:8080/maps/latest/xyz-maps-core.min.js" type="text/javascript" charset="UTF-8" ></script>
          <script src="https://localhost:8080/maps/latest/xyz-maps-display.min.js" type="text/javascript" charset="UTF-8" ></script>
          <!-- include this if you want to use an MVT basemap -->
          <script src="https://localhost:8080/maps/latest/xyz-maps-plugins.min.js" type="text/javascript" charset="UTF-8" ></script>
        </head>
    ```

1. Add a div element to body that can act as the display container

    ```html
    <body>
      <div style="width: 960px; height: 540px" id="map"></div>
    </body>
    ```

1. Create a basic Map Layer/Provider and setup visibility

    ```javascript
    <script type="application/javascript">
      //specify your credentials to spaces
      var YOUR_ACCESS_TOKEN = "abcdef"; // <--- TODO: Replace this with your token

      // configure layers
      var layers = [
        // TODO 
      ]
    </script>
    ```

1. Initialize the Map with Layer config and define the starting location

    ```javascript
      // setup the Map Display
      window.display = new  here.xyz.maps.Map( document.getElementById("map"), {
          zoomLevel : 17,
          center: {
              longitude: -117.15406, latitude: 32.72966
          },
          // add layers to display
          layers: layers
      });
    ```

1. Congratulations! Your first XYZ Maps map is ready
