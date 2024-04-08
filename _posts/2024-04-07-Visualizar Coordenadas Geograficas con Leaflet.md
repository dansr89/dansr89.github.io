# Visualizar Coordenadas Geograficas con Leaflet

Este sera el primer post en este lugar, la idea de este blog es tener un lugar donde pueda guardar notas tecnicas de algunos proyectos personales en los que estoy trabajando. Lo escribo en español porque para variar la documentacion en nuestro idioma es escasa, y aunque no espero que sea de utilidad para alguien, nunca se sabe :) 



### <ins>Leaflet</ins>

Leaflet es una biblioteca de JavaScript utilizada para crear mapas web interactivos. Con Leaflet, se puede crear un mapa simple usando solo dos o tres expresiones JavaScript, Justo lo que requiero.



Descargar y descomprimir Leaflet:

```bash
mkdir geo
cd geo
wget https://leafletjs-cdn.s3.amazonaws.com/content/leaflet/v1.8.0/leaflet.zip
unzip leaflet.zip
```

Se crea un html dentro del mismo path y se declara la ruta del .css y del .js de la siguiente forma
      
```bash
<!DOCTYPE html>
<html>
<head>
    <title>Mapa Basico con Marcadores y Popup</title>
    <meta name="viewport" content="width=device-width, 
        initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <link rel="stylesheet" href="leaflet.css">
    <script src="leaflet.js"></script>
    <style>
        body {
            padding: 0;
            margin: 0;
        }
        html, body, #map {
            height: 90%;
            width: 88%;
        }
    </style>
</head>
```

Se establecen las coordenadas del mapa inicial y el zoom

```bash
    <div id="map"></div>
    <script>
        let map = L.map("map", {center: [19.6341807,-99.2573259], zoom: 16});
        L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {attribution: ' <a href="http://' + '"></a>'}
        ).addTo(map);
```



![](https://github.com/dansr89/dansr89.github.io/blob/main/p1img/map1.png?raw=true)


Ahora para marcar varias coordenadas en el mapa usamos un arreglo y un FOR para recorrer el arreglo y llamar a L.circleMarker

```bash
// Arreglo para multiples puntos y texto en el popup 
var coordinates = [
    [19.6341807,-99.2573259,"Ejemplo1"],
    [19.6353249,-99.2532091,"Ejemplo2"],
    [19.636679,-99.2556338,"Ejemplo3"]

];
var layerGroup = L.layerGroup().addTo(map);
for (i = 0; i < coordinates.length; i++) {
    marker = L.circleMarker([coordinates[i][0], coordinates[i][1]], {radius: 7, color: "black", fillColor: "black"});
    layerGroup.addLayer(marker);
}
```

![](https://github.com/dansr89/dansr89.github.io/blob/main/p1img/map2.png?raw=true)


Necesitaba generar popups en cada marcador y que contengan una imagen con descripcion de la misma, para esto es el campo que en el arreglo llene con las cadenas "EjemploX" , la idea es generar un campo extra en el arreglo, con las URLs de las imagenes.

```bash
// Pinta popups con imagenes y Texto
    marker.bindPopup("<img src=https://www.openstreetmap.org/assets/osm_logo-4afddaae0230a5a46687fdc751ed256dfdccde144118cb02a7d7960f207a4b92.svg> Comentario: " + coordinates[i][2] );
    layerGroup.addLayer(marker);
}
```

![](https://github.com/dansr89/dansr89.github.io/blob/main/p1img/map3.png?raw=true)


Codigo Completo:

```bash
<!DOCTYPE html>
<html>
<head>
    <title>Mapa Basico con Marcadores y Popup</title>
    <meta name="viewport" content="width=device-width, 
        initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <link rel="stylesheet" href="leaflet.css">
    <script src="leaflet.js"></script>
    <style>
        body {
            padding: 0;
            margin: 0;
        }
        html, body, #map {
            height: 90%;
            width: 88%;
        }
    </style>
</head>
<body>
    <div id="map"></div>
    <script>
        let map = L.map("map", {center: [19.6341807,-99.2573259], zoom: 16});
        L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {attribution: ' <a href="http://' + '"></a>'}
        ).addTo(map);
// Arreglo para multiples puntos y texto en el popup 
var coordinates = [
    [19.6341807,-99.2573259,"Ejemplo1"],
    [19.6353249,-99.2532091,"Ejemplo2"],
    [19.636679,-99.2556338,"Ejemplo3"]

];
var layerGroup = L.layerGroup().addTo(map);
for (i = 0; i < coordinates.length; i++) {
    marker = L.circleMarker([coordinates[i][0], coordinates[i][1]], {radius: 7, color: "black", fillColor: "black"});
// Pinta popups con imagenes y Texto
    marker.bindPopup("<img src=https://www.openstreetmap.org/assets/osm_logo-4afddaae0230a5a46687fdc751ed256dfdccde144118cb02a7d7960f207a4b92.svg> Comentario: " + coordinates[i][2] );
    layerGroup.addLayer(marker);
}
    </script>
</body>
</html>

```









