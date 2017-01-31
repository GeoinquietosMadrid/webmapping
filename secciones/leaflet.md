# Leaflet.js

<!-- MarkdownTOC -->

- Intro to LeafletJS
- Getting started
- Adding a GeoJSON layer
- Styling a GeoJSON layer
- Adding a Pop-up

<!-- /MarkdownTOC -->

## Intro to LeafletJS

## Getting started

Creating a basic map with Leaflet is actually pretty easy, this Javascript snippet will create a map with a single marker and a popup:

```javascript
var map = L.map('map').setView([51.505, -0.09], 13);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);

L.marker([51.5, -0.09]).addTo(map)
    .bindPopup('A pretty CSS3 popup.<br> Easily customizable.')
    .openPopup();
```

Let's see what each part does:

### [Map object](http://leafletjs.com/reference-1.0.3.html#map)

```javascript
var map = L.map('map').setView([51.505, -0.09], 13);
```

There are three different `map` on that single line! let's elaborate a bit: 

* `var map`: This is the variable that will hold the map object
* `L.map`: This makes reference to the [Leaflet map class](http://leafletjs.com/reference-1.0.3.html#map)
* `'map'`: This is the HTML DOM object where we'll render the map

This line uses Leaflet's Map class for creating a new `map` object on the DOM element identified by `'map'`. 

The `setView` method is necessary in order to center the map to an specific location and zoom level. 

### [Tiled layer](http://leafletjs.com/reference-1.0.3.html#tilelayer)

Most tiled web maps follow certain Google Maps conventions:

* Tiles are 256x256 pixels
* At the outer most zoom level, 0, the entire world can be rendered in a single map tile.
* Each zoom level doubles in both dimensions, so a single tile is replaced by 4 tiles when zooming in. This means that about 22 zoom levels are sufficient for most practical purposes.
* The Web Mercator projection is used, with latitude limits of around 85 degrees.
* The _de facto_ OpenStreetMap standard, known as Slippy Map Tilenames or XYZ follows these and adds more:
  * An X and Y numbering scheme
  * PNG images for tiles
  * Images are served through a REST API, with a URL like `http(s)://.../Z/X/Y.png`, where Z is the zoom level, and X and Y identify the tile.

  (from [Wikipedia: Tiled web map](https://en.wikipedia.org/wiki/Tiled_web_map))


> Check [this link](https://www.mapbox.com/help/how-web-maps-work/) to know more about tiles and how they work

This is the code that let us add a tiled layer to a leaflet map: 

```javascript
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);
```

* Remember to always add the attribution
* `.addTo()` is a method of the `tileLayer` class (and many others) that adds the declared layer to the map object. It expects the variable with the map object as a parameter. 

> Check [this tiled layers catalog](http://leaflet-extras.github.io/leaflet-providers/preview/) to find more basemap options.

### [Marker](http://leafletjs.com/reference-1.0.3.html#marker)

Adding a single marker to a Leaflet map is as easy as: 

```javascript
L.marker([51.5, -0.09]).addTo(map)
    .bindPopup('A pretty CSS3 popup.<br> Easily customizable.')
    .openPopup();
```

This adds a marker as a new layer to the map. It expects at least an array with pair of **LatLon** coordinates. 

`.bindPopup()` adds a popup with custom HTML content inside. `.openPopup()` opens the popup programmatically. 

##### Check a live version of this basic example [here](http://plnkr.co/edit/cDszbYcgUZexjCPzoSmT?p=preview). Feel free to play with it!

## Adding a GeoJSON layer
Use this [Spanish cities dataset](../src/populated_places.geojson)

## Styling a GeoJSON layer
Bubbles map

## Adding a Pop-up
Show some info for each feature