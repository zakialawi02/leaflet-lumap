# Leaflet Lumap
 ![Leaflet Lumap - Luar Map](lumap-thumbnail.jpg)
## How to usage
#### - Install / Include Bootsrap 5 
for full documentation can visit to : https://getbootstrap.com/docs/5.3/getting-started/introduction/

#### - Install / Include Bootsrap Icon 
for full documentation can visit to : https://icons.getbootstrap.com/

#### - Activate plugins
include the stylesheet 
```html
<link rel="stylesheet" href="css/leaflet.lumap.css"/>
```
include the javascript 
```html
<script src="js/leaflet.lumap.js"></script>
```
to use plugins please load using this method
- Config variabel Map
```js
let map = L.map('map').setView([39.73, -104.99], 13);
```
- Describe selector/element 
```js
let elLumap = document.querySelector('#lumap');
```

- Config as Base Maps
```js
let baseMaps = {
	id:'basemap',
	title : 'BaseMaps',
	type : 'single',
	child : [
		{
			title : "OpenStreetMap",
			iconHtml : `<img src="https://cdn-icons-png.flaticon.com/512/5088/5088218.png">`,
			layer : osm
		},
		{
			title : 'Satellite',
			iconHtml : `<img src="https://cdn-icons-png.flaticon.com/512/5088/5088218.png">`,
		    layer : satellite
		}
	]
}
```

- Config as Overlay Maps
```js
let littleton = L.marker([39.61, -105.02]).bindPopup('This is Littleton, CO.');
let denver    = L.marker([39.74, -104.99]).bindPopup('This is Denver, CO.');
let aurora    = L.marker([39.73, -104.8]).bindPopup('This is Aurora, CO.');
let golden    = L.marker([39.77, -105.23]).bindPopup('This is Golden, CO.');
let cities = L.layerGroup([littleton, denver, aurora, golden]);
var overlayMaps = {
		id:'layers',
		title : 'Layers',
		child : [
				{
				    title: "Cities",
				    icon:'house',
				    style:'background:#9c89b8;color:#fff',
				    layer:cities
				}
			]
	};
```
- Create the Lumap instance
```js
let lumap = new Lumap(map,elLumap,[baseMaps,overlayMaps]);
```