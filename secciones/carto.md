# CARTO.JS
<!-- MarkdownTOC -->

- How does CARTO.js works with Leaflet
- Adding a CARTO layer
- Styling a CARTO.js layer
- Filtering a layer with CARTO
- Changing a visualization on runtime
- Popups with CARTO.js
- LIVE EXAMPLE

<!-- /MarkdownTOC -->

## How does CARTO.js works with Leaflet

CARTO.js is a Javascript library that works over Leaflet or Google Maps API and allows to interact with CARTO cloud-based backend to instantiate and retrieve data driven tiled map layers along with other associated data. 

### Tiled layers vs. Leaflet vectors

When loading a lot of vector layers to a Leaflet map we can easily fall into a performance problem, as each feature of each layer has to be stored in the browser's memory. 

Then, what's the alternative if we need to visualize thousands or even millions of points at the same time? 

We need a map server that is optimized for the task. 

There are many types of map servers and companies that provide such services. One of those is CARTO.

How does CARTO work? (at a very high level)

* Data is stored on a cloud database
* Browser sends a request to the server to instantiate a map 
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

Each of those parameters could be used to configure the styling, filters and Popups


## Styling a CARTO.js layer

As mentioned before, CARTO layers are styled using [CartoCSS](https://carto.com/docs/carto-engine/cartocss).

This is what a default CartoCSS block code looks like: 

```css
#layer{
    marker-fill-opacity: 0.9;
    marker-line-color: #FFF;
    marker-line-width: 1;
    marker-line-opacity: 1;
    marker-placement: point;
    marker-type: ellipse;
    marker-width: 10;
    marker-fill: #FF6600;
    marker-allow-overlap: true;
}
``` 

Properties are pretty much self-explanatory, but there is much more that could be done with just a few tricks: 

### Conditional styling

CartoCSS supports conditional expressions in order to apply different styles to features depending on column values: 

```css
#layer{
    marker-fill-opacity: 0.6;
    marker-line-color: #000;
    marker-line-width: 0.3;
    marker-line-opacity: 0.5;
    marker-placement: point;
    marker-type: ellipse;
    marker-allow-overlap: true;
    marker-width:10;
    marker-fill:#FF6600;

    [pop_max>1000000]{
        marker-width:18;
    }
    [pop_max>5000000]{
        marker-width:26;
    }
    [featurecla='Admin-0 capital']{
        marker-fill:#0099FF;
    }
}
```

That code block generates a visualization where the size of the marker depends on the population, and the color depends on the `featurecla` column value.

Remember that CartoCSS is interpreted from top to bottom, so be careful with the conditions order!

### Zoom based conditions

A very useful CartoCSS rule is using the current zoom level as a condition: 

```css
#layer{
    marker-fill-opacity: 0.6;
    marker-line-color: #000;
    marker-line-width: 0.3;
    marker-line-opacity: 0.5;
    marker-placement: point;
    marker-type: ellipse;
    marker-allow-overlap: true;
    
    marker-fill:#FF6600;
    [featurecla='Admin-0 capital']{
        marker-fill:#0099FF;
    }
    
    marker-width:10;
    [pop_max>1000000]{
        marker-width:18;
    }
    [pop_max>5000000]{
        marker-width:26;
    }

    [zoom>6]{
        marker-width:30;
        [pop_max>1000000]{
            marker-width:54;
        }

        [pop_max>5000000]{
            marker-width:78;
        }
    }
}
```

### TurboCARTO

So that's easy for a very simple map, but for more complex choropleth maps, graduated symbols, zoom levels, etc. we'd need multiple nested conditions and the CartoCSS code can become a real pain. 

TurboCARTO is a CartoCSS pre-processor that simplifies the task a lot. A `ramp()` function expects a column, a range of values or colors and a classification method. This way, we can translate several blocks of code into a single line. It's also dynamic, so your visualization is meaningful regardless of the filter/zoom level. 

```css
#layer {
  marker-width: ramp([pop_max], range(4, 16), quantiles(5));
  marker-fill: ramp([featurecla], (#5B3F95, #1D6996, #129C63, #73AF48, #EDAD08, #E17C05, #C94034, #BA0040), category(8));
  marker-fill-opacity: 1;
  marker-allow-overlap: true;
  marker-line-width: 0.3;
  marker-line-color: #000;
  marker-line-opacity: 0.5;
}
```

Click [here](https://carto.com/blog/styling-with-turbo-carto) to learn more about TurboCARTO. And [here](https://github.com/CartoDB/turbo-carto) is the source code (it's Open Source!)

## Filtering a layer with CARTO

As we said before, CARTO only renders the result from the SQL query that defines the sublayer.

That makes very easy to filter the data: 


```sql
SELECT * FROM ne_10m_populated_places_simple WHERE pop_max>100000
```

That query filters out cities with less than `100000` inhabitants. 

```sql
SELECT * FROM ne_10m_populated_places_simple WHERE featurecla NOT LIKE '% capital'
```

That filters out cities that are either `Admin-0` or `Admin-1` capital

```sql
SELECT * FROM ne_10m_populated_places_simple WHERE name ILIKE 'Madrid'
```

That will only return the data for Madrid

The only requirement here is that `the_geom` is present in the selection. Also `cartodb_id` is necessary for interactivity (more on that later)

## Changing a visualization on runtime

What if we need to set a dynamic filter? Or change the marker color on user interaction? 

We could use a handful of methods that allow to change some visualization parameters at anytime: 

* `sublayer.set()`: set a complete layersource configuration object
* `sublayer.setSQL()`: set a different SQL query for the sublayer
* `sublayer.setCartoCSS()`: set a different CartoCSS code for the sublayer

This is specially useful in combination with jQuery for creating some interactive visualizations:

```javascript
$('#blue').click(function() {
    //do stuff
    layer.getSubLayer(0).setCartoCSS('#layer{marker-fill:#00F;}')
});
```

That changes all markers' color to blue

Using jQuery to capture the value of an input field and then use it as a SQL filter:

```javascript
$('#apply_filter').click(function (){
    //do stuff
    var filter=$('#pop_filter').val();
    layer.getSubLayer(0).setSQL('SELECT * FROM ne_10m_populated_places_simple WHERE pop_max >='+filter)
});
```

## Popups with CARTO.js

In order to create a Popup that shows data from the table, we need the following:

```javascript
cdb.vis.Vis.addInfowindow(
    map, 
    layer.getSubLayer(0), 
    ['cartodb_id', 'name', 'pop_max', 'featurecla'],
    {infowindowTemplate: $('#popup_template').html()}
);
```

Also, set the proper interactivity for the sublayer: 

```javascript
var layerSource={
    user_name: 'carto-workshops',
    type: 'cartodb',
    sublayers: [{
        sql: 'SELECT * FROM ne_10m_populated_places_simple',
        cartocss: $('#cartoCSS').html(),
        interactivity: 'cartodb_id, name, pop_max, featurecla'
    }]
}
```

We're also using jQuery to get the `popup_template` element and pass it as a parameter for creating the Popup. 

This is the where we set the popup content, using [Mustache](https://mustache.github.io/mustache.5.html) templates

```html
<div class="cartodb-popup-content">
    <h1>{{content.data.name}}</h1>
    <h3>{{content.data.featurecla}}</h3>
    <b>Population: </b>
    {{content.data.pop_max}}
</div>
```

## [LIVE EXAMPLE](http://plnkr.co/edit/U2IkgC4BbN3FkOJnaj1u?p=preview)




























