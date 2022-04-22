# Leaflet.awesome-svg-markers plugin v3.0
Leaflet AwesomeSVGMarkers - allows you to display custom icons easily using Leaflet, now also using SVG icons

Version 3.0 of Leaflet.awesome-svg-markers is tested with:
- Bootstrap 5.1
- Font Awesome 5.15
- Ionicons 6.0
- Leaflet 1.7.1
- Ionic 6.1
	
<a href="http://jsfiddle.net/VPzu4/92/" target="_blank">JSfiddle demo</a> 

## Bootstrap/Font-Awesome icons
This plugin depends on either Bootstrap, Font-Awesome, or Ionicons for the rendering of the icons. See these urls for more information:

For Font-Awesome
- [https://fontawesome.com/]()

For Twitter bootstrap:
- [http://getbootstrap.com/getting-started/]()

## Using the plugin with Font Awesome or Bootstrap
- 1) First, follow the steps for including Font-Awesome or Twitter bootstrap or Ionicons into your application.

For Font-Awesome, steps are located here:

[https://fontawesome.com/start]()

For Bootstrap, steps are here:

[http://getbootstrap.com/getting-started/]()
    
````xml
<link rel="stylesheet" href="http://code.ionicframework.com/ionicons/1.5.2/css/ionicons.min.css">
````

- 2) Next, copy the dist/images directory, awesome-markers.css, and awesome-markers.js to your project and include them:
````xml
<link rel="stylesheet" href="css/leaflet.awesome-svg-markers.css">
````
````xml
<script src="js/leaflet.awesome-svg-markers.js"></script>
````

- 3) Now use the plugin to create a marker like this:
````js
  // Creates a red marker with the coffee icon
  var redMarker = L.AwesomeSVGMarkers.icon({
    icon: 'coffee',
    markerColor: 'red'
  });
      
  L.marker([51.941196,4.512291], {icon: redMarker}).addTo(map);
````

### Properties

| Property        | Description                                     | Default Value | Possible  values |
| --------------- | ----------------------------------------------- | ------------- |----------------- |
| icon            | Name of the icon                                | 'home'        | See glyphicons or font-awesome |
| prefix          | Select de icon library                          | 'glyphicon'   | 'fa' for font-awesome or 'glyphicon' for bootstrap 3 |
| markerColor     | Color of the marker                             | 'blue'        | 'white', 'red','darkred', 'lightred', 'orange', 'beige', 'green', 'darkgreen', 'lightgreen', 'blue', 'darkblue', 'lightblue', 'purple', 'darkpurple', 'pink', 'cadetblue', 'white', 'gray', 'lightgray', 'black' |
| iconColor       | Color of the icon                               | 'white'       | 'white', 'black' or css code (hex, rgba etc) |
| spin            | Make the icon spin                              | false         | true or false. Font-awesome required | 
| extraClasses    | Additional classes in the created &lt;i&gt; tag | ''            | 'fa-rotate90 myclass' or other custom configuration |


### Supported icons
The 'icon' property supports these strings:
- 'home'
- 'glass'
- 'flag'
- 'star'
- 'bookmark'
- .... and many more, see: http://fortawesome.github.io/Font-Awesome/icons/
- Or: http://getbootstrap.com/components/#glyphicons
- Or: http://ionicons.com

### Tips & Tricks

Tweak size and positioning of the icons:

````css
    .awesome-marker i {
        font-size: 18px;
        margin-top: 8px;
    }
````

## SVG Icons

## Using the plugin with Ionicons + a framework

Awesome SVG Markers offers support for [Ionicons](https://ionic.io/ionicons) when used with a framework of your choice. Please note that simply importing the library into a HTML document will most likely fail.

Start by importing the necessary libraries:

```js
import {
  accessibility     // We're importing the accessibility icon here. You can import whichever icon you want
} from 'ionicons/icons';
import L from "leaflet";
import "leaflet/dist/leaflet.css";
import "leaflet.awesome-svg-markers/dist/leaflet.awesome-svg-markers.css";
import "leaflet.awesome-svg-markers";
```

Set up a simple map:

```js
const map = L.map("mapContainer", { zoomControl: false})    // Given that the HTML document has an element with a mapContainer ID
      .setView([55.6, 13], 15);

L.tileLayer("http://{s}.tile.osm.org/{z}/{x}/{y}.png", {
      attribution:
        '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
    }).addTo(map);
```

Create an SVG icon based on the Ionics icon imported above:

```js
const myIcon = L.AwesomeMarkers.icon({
        svgIcon: accessibility,     // The Ionicon icon, which contains an SVG object
        markerColor: 'green',
        iconColor: '#ccc'
      });
```

Finally, add the icon to the map:

```js
    L.marker( [55.6, 13], {icon: myIcon}).addTo(map);
```


### Your own SVG icons

You can use your own SVG icons as well. This can be done without a framework. An [example of this](examples/svg-example.html) is available.

### Properties

| Property        | Description                                        | Default Value | Possible  values |
| --------------- | -------------------------------------------------- | ------------- | ---------------- |
| svgIcon         | An SVG object, e.g. an Ionicon icon                | undefined     | |
| markerColor     | Color of the marker                                | 'blue'        |  'white', 'red','darkred', 'lightred', 'orange', 'beige', 'green', 'darkgreen', 'lightgreen', 'blue', 'darkblue', 'lightblue', 'purple', 'darkpurple', 'pink', 'cadetblue', 'white', 'gray', 'lightgray', 'black' |
| iconColor       | Color of the icon                                  | 'white'       | 'white', 'black' or css code (hex, rgba etc) |
| extraClasses    | Additional classes in the created &lt;span&gt; tag | ''            | 'fa-rotate90 myclass' or other custom configuration |

### Tips & Tricks

Tweak size and positioning of the icons:

````css
    .awesome-marker svg {
        margin-top: 10px;
        width: 16px;
    }
````
## License
- Leaflet.AwesomeSVGMarkers and colored markers are licensed under the ISC License - [https://opensource.org/licenses/ISC]().
- Font Awesome: [https://fontawesome.com/license]()
- Bootstrap: [http://getbootstrap.com/]()
- Ionicons: [http://ionicons.com]()
