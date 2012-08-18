# OpenLayers Instrumenter

A small library that instruments OpenLayers dynamically to create a custom build based on actual usage.

## Usage

### Installation and instrumentation

Add the script before OpenLayers:

```html
<script src="lib/OpenLayers-2.12/lib/OpenLayers.js"></script>
<script src="openlayers-instrumenter.js"></script>
```

It will instrument OpenLayers. 2 seconds after loading it will console.log the custom profile and instructions for creating a profile spanning usage on multiple pages.

The custom profile output looks something like this:

```
[first]

[last]

[include]
OpenLayers/Map.js
OpenLayers/BaseTypes/Size.js
OpenLayers/BaseTypes/Bounds.js
OpenLayers/Util.js
OpenLayers/BaseTypes/Element.js
OpenLayers/Events.js
OpenLayers/Function.js
OpenLayers/Event.js
OpenLayers/String.js
OpenLayers/Control/Navigation.js
OpenLayers/Control/Zoom.js
OpenLayers/Control/ArgParser.js
OpenLayers/Control/Attribution.js
OpenLayers/Handler/Click.js
OpenLayers/Control/DragPan.js
OpenLayers/Control/ZoomBox.js
OpenLayers/Handler/Drag.js
OpenLayers/Handler/Box.js
OpenLayers/Handler/MouseWheel.js
OpenLayers/Control/PinchZoom.js
OpenLayers/Handler/Pinch.js
OpenLayers/Events/buttonclick.js
OpenLayers/Layer/WMS.js
OpenLayers/Layer/Vector.js
OpenLayers/Renderer/SVG.js
OpenLayers/StyleMap.js
OpenLayers/Style.js
OpenLayers/Projection.js
OpenLayers/Control/LayerSwitcher.js
OpenLayers/Lang.js
OpenLayers/Control/MousePosition.js
OpenLayers/Control/DrawFeature.js
OpenLayers/Handler/Point.js
OpenLayers/Handler/Path.js
OpenLayers/Handler/Polygon.js
OpenLayers/Handler/RegularPolygon.js
OpenLayers/BaseTypes/LonLat.js
OpenLayers/Animation.js
OpenLayers/BaseTypes/Pixel.js

[exclude]

```

### Creating a custom profile

Create `OpenLayers-2.12/build/custom.cfg` and save the output in there. Then do:

```sh
$ cd OpenLayers-2.12/build/
$ ./build.py custom
```

The compiled file is put in `OpenLayers-2.12/build/OpenLayers.js`. The full build includes *261 files* weighing in at whopping *942 KB* (minified!). For the example page provided, the custom build is reduced to *60 files* totaling *271 KB*.

## Example

Check out `example.html` for usage. `example-custom.html` uses the custom build to show the difference in page weight and that the custom profile actually works.

## License

MIT
