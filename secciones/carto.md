# CARTO.JS
<!-- MarkdownTOC -->

- How does CARTO.js works with Leaflet
- Adding a CARTO layer

<!-- /MarkdownTOC -->

## How does CARTO.js works with Leaflet

CARTO.js is a Javascript library that works over Leaflet or Google Maps API and allows to interact with CARTO cloud-based backend to instantiate and retrieve data driven tiled map layers along with other associated data. 

### Tiled layers vs. Leaflet vectors

When loading a lot of vector layers to a Leaflet map we can easily fall into a performance problem, as each feature of each layer has to be present in the browser's memory. 

Then, what's the alternative if we need to visualize thousands or even millions of points at the same time? 

We need a map server that is optimized for the task. 

There are many types of map servers and companies that provide such services. One of those is CARTO.

How does CARTO work? (at a very high level)

* Data is stored on a cloud database
* Browser send a request to instantiate a map to the server
* Server parses the request, fetch the data and renders the tiles
* Tiles are served
* Browser arranges tiles and displays them as part of the HTML document

There are also several layers of cache and many other moving pieces, but let's keep it simple for now. 

### CARTO layers

* A CARTO layer is a layer that you could add to a Leaflet map in order to visualize data that is hosted on CARTO cloud databases. 
* Each CARTO layer has one or more sublayers. 
* Each sublayer is defined by two basic parameters: 

	* **SQL query:** The query that will be used to fetch data from the PostgreSQL database that backs every CARTO account.
	* **CartoCSS style:** The style rules that will be used to 'draw' the map tiles.
* A relevant point here is that **CARTO renders the result from SQL queries**, not tables, files or any other set of geographic information. 
* As a consequence, everything must be imported to CARTO database before creating a map.

## Adding a CARTO layer

So, having this Leaflet map with a tile layer already added: 

```javascript
var map= new L.Map('map', {
    zoom:3,
    center:[12,0]
});

L.tileLayer('https://cartodb-basemaps-d.global.ssl.fastly.net/dark_all/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, &copy; <a href="http://cartodb.com/attributions">CartoDB</a>'
})
.addTo(map);
```

We can add a CARTO layer using [`createLayer()`](https://carto.com/docs/carto-engine/carto-js/api-methods#cartodbcreatelayermap-layersource--options--callback) method, this is the basic structure: 

```javascript
cartodb.createLayer(map, layerSource,{
 	//layer options
})
.addTo(map)
```

From that code block: 

* `map` is the Leaflet map object
* `layerSource` is a variable that contains all configuration for the layer

How does a layer source looks like? 

```javascript
var layerSource={
    user_name: 'carto-workshops',
    type: 'cartodb',
    sublayers: [{
        sql: 'SELECT * FROM ne_10m_populated_places_simple',
        cartocss: $('#cartoCSS').html(),
        interactivity: 'cartodb_id'
    }]
}
```

As you see, it contains: 

* `user_name` to identify the CARTO account (database) to fetch data from
* `sublayers` is an array that contains one or more sublayer definition, for each sublayer, we have:
	* `sql` (required)
	* `cartocss` (required)
	* `interactivity` (optional)

