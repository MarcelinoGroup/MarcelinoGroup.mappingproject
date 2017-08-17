<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8' />
    <title></title>
    <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
    <link href="https://fonts.googleapis.com/css?family=Open+Sans" rel="stylesheet">
    <script src='https://api.tiles.mapbox.com/mapbox-gl-js/v0.38.0/mapbox-gl.js'></script>
    <link href='https://api.tiles.mapbox.com/mapbox-gl-js/v0.38.0/mapbox-gl.css' rel='stylesheet' />
    <style>
      body {
        margin: 0;
        padding: 0;
      }

      #map {
        position: absolute;
        top: 0;
        bottom: 0;
        width: 100%;
      }
      .marker {
  background-image: url('pin-in-the-map.png');
  background-size: cover;
  width: 30px;
  height: 30px;
  border-radius: 50%;
  cursor: pointer;
}
.mapboxgl-popup {
  max-width: 400px;
}

.mapboxgl-popup-content {
  text-align: left;
  font-family: 'Open Sans', sans-serif;
}
    </style>
</head>
<body>

<div id='map'></div>

<script>

mapboxgl.accessToken = 'pk.eyJ1Ijoic2FtYWxsbnV0dCIsImEiOiJjajYzdXBlNncxajJqMnFxN2xoNGlyanhyIn0.dAmU5HZqyC4r3sY09mgHDA';

var map = new mapboxgl.Map({
  container: 'map',
  style: 'mapbox://styles/samallnutt/cj63uq5n64pvg2ro53nvtuxbc',
  center: [0, 0],
  zoom: 1
});

map.dragRotate.disable();
map.touchZoomRotate.disableRotation();
map.transform.lngRange = [-180, 180];
map.transform.latRange = [-60, 70];


var geojson = {
  type: 'FeatureCollection',
  features: [{
    type: 'Feature',
    geometry: {
      type: 'Point',
      coordinates: [116.73, 20.7]
    },
    properties: {
      title: 'Dongsha Atoll, 4 Records',
      description: 'Acropora sp., Pavona sp., Porites sp., Stylophora sp.'
    }
  },

  {
   type: 'Feature',
   geometry: {
    type: 'Point',
    coordinates: [-90.31,-0.74]
  },
  properties: {
    title: 'Galapagos, 1 Record',
    description: 'Pavona Clavus'
  }
},

{
    type: 'Feature',
    geometry: {
      type: 'Point',
      coordinates: [-74.11, 11.33]
    },
    properties: {
      title: 'Colombia, 8 Records',
      description: 'Montastraea cavernosa, Orbicella faveolata, Orbicella franksi, Diploria strigosa, Diploria Labyrinthiformis, Colpophylla natans, Porites astreoides, Siderastrea siderea'
    }
  },

  {
  type: 'Feature',
  geometry: {
    type: 'Point',
    coordinates: [95.33,5.83]
  },
  properties: {
    title: 'Pulau Weh Island, 20 Records',
    description: 'Acropora sp., Pocillopora sp., Hydnophora sp., Echinopora sp., Favites sp., Symphyllia sp., Platygyra sp., Galaxea sp., Favia sp., Porites sp.(2), Fungia sp., Pavona sp., Acanthastrea sp., Goniastrea sp., Cyphastrea sp., Goniopora sp., Montastraea sp., Montipora sp., Diplostrea sp.'
  }
},

  {
  type: 'Feature',
  geometry: {
    type: 'Point',
    coordinates: [103.83,1.17]
  },
  properties: {
    title: 'Singapore, 59 Records',
    description: 'Acropora sp.(3), Pocillopora sp.(3), Hydnophora sp.(3), Echinopora sp.(2), Favites sp.(3), Symphyllia sp.(3), Platygyra sp.(3), Galaxea sp.(3), Favia sp.(2), Porites sp.(5), Fungia sp.(3), Pavona sp.(3), Acanthastrea sp.(2), Goniastrea sp.(3), Cyphastrea sp.(2), Goniopora sp.(2), Montastraea sp.(2), Montipora sp.(3), Diplostrea sp.(2), Merulina sp., Echnopora sp., Favia sp., Ctenactis sp., Pectinia sp., Podobacia sp., Pachyseris sp.'
  }
},

  {
    type: 'Feature',
    geometry: {
      type: 'Point',
      coordinates: [-66.093,18.255]
    },
    properties: {
      title: 'Puerto Rico, 16 Records',
      description: 'Siderastrea siderea, Montastraea franski, Diploria strigosa, Agaricia tenuifolia, Porites porites(2), Agaricia agaricites, Montastraea faveolata, Montastraea cavernosa, Montastraea annularis, Diploria labyrinthiformis, Erythropodium caribaeorum, Millepora complanata, Millepora alcicornis, Acropora cervicornis, Mycetophyllia ferox'
    }
},

{
  type: 'Feature',
  geometry: {
    type: 'Point',
    coordinates: [147.034,-18.457]
  },
  properties: {
    title: 'Central Great Barrier Reef, 19 Records',
    description: 'Acropora millepora, Acropora latistella, Acropora subulata, Turbinaria mesenterina, Acropora sp.(3), Pocillopora sp.(3), Porites sp.(3), Faviidae sp., Mussidae sp., Acropora hyancinthus sp., Acropora millepora sp., Platygyra daedalea sp., Porites lobata sp.'
  }
},

{
  type: 'Feature',
  geometry: {
    type: 'Point',
    coordinates: [-157.947,21.457]
  },
  properties: {
    title: 'Oahu Island, 6 Records',
    description: 'Pavona varians, Pocillopora meandrina, Porites lobata, Montipora capitata, Cyphastrea ocellina, Porites compressa'
  }
},

{
  type: 'Feature',
  geometry: {
    type: 'Point',
    coordinates: [98.378,7.774]
  },
  properties: {
    title: 'Phuket Island, Thailand, 104 Records',
    description: 'Echinopora sp.(4), Pocillopora damicornis(4), Diplostrea heliopora(4), Acropora sp.(4), Montipora sp.(4), Goniopora sp.(4), Pavona sp.(4), Leptastrea sp.(4), Coeloseris sp.(4), Pachyseris sp.(4), Ctenactis sp.(4), Favites sp.(4), Psammocora sp.(4), Symphyllia sp.(4), Porites sp.(8), Turbinarea sp.(4), Galaxea sp.(4), Podacacia sp.(4), Platygyra sp.(4), Merulina sp.(4), Dipsastraea sp.(4), Herpolitha sp.(4), Goniastrea sp.(4), Pectinia sp.(4), Fungia sp.(4)'
  }
},

{
  type: 'Feature',
  geometry: {
    type: 'Point',
    coordinates: [-61.311,15.251]
  },
  properties: {
    title: 'Dominica, 23 Records',
    description: 'Stephanocoenia intersepta, Madracis mirabilis, Madracis decactis, Acropora palmata, Siderastrea siderea, Agaricia agaricites, Meandrina meandrites, Meandrina brasiliensis, Dichocoenia stokesi, Dendrogyra cylindrus, Mussa angulosa, Isophyllia sinuosa, Colpophyllia natans, Diploria strigosa, Diploria clivosa, Diploria labyrinthiformis, Montastraea annularis, Montastraea faveolata, Montastraea cavernosa, Eusmilia fastigiata, Porites porites, Porites atsreoides, Millepora sp.'
  }
},

{
  type: 'Feature',
  geometry: {
    type: 'Point',
    coordinates: [115.47,-32.03]
  },
  properties: {
    title: 'Rottnest Island, 1 Record',
    description: 'Coscinaraea marshae'
  }
},

{
  type: 'Feature',
  geometry: {
    type: 'Point',
    coordinates: [-149.706,-17.574]
  },
  properties: {
    title: 'French Polynesia, 2 Records',
    description: 'Pocillopora verrucosa, Acropora elseyi'
  }
},

{
  type: 'Feature',
  geometry: {
    type: 'Point',
    coordinates: [-59.624,13.087]
  },
  properties: {
    title: 'Barbados, 5 Records',
    description: 'Montastraea annularis, Siderastrea siderea, Montastraea cavernos, Diploria sp., Porites astreoides'
  }
},

{
  type: 'Feature',
  geometry: {
    type: 'Point',
    coordinates: [9.83,44.02]
  },
  properties: {
    title: 'Gulf of La Spezia, 1 Record',
    description: 'Paramuricea clavata'
  }
},

{
  type: 'Feature',
  geometry: {
    type: 'Point',
    coordinates: [114.175,-21.865]
  },
  properties: {
    title: 'Bundegi Reef, 2 Records',
    description: 'Acropora sp., Montipora sp.'
  }
},

{
  type: 'Feature',
  geometry: {
    type: 'Point',
    coordinates: [39.825,-4.042]
  },
  properties: {
    title: 'Kenya, 5 Records',
    description: 'Porites sp.(3), Acropora sp., Pocillopora sp.'
  }
},

{
  type: 'Feature',
  geometry: {
    type: 'Point',
    coordinates: [-75.011,18.426]
  },
  properties: {
    title: 'Navassa Island Wildlife Refuge, 8 Records',
    description: 'Montastraea faveolata, Agaricia sp., Siderastrea siderea, Diplora sp., Porites porites, Porites asteroides, Montastraea cavernosa, Agaricia palmata'
  }
},

{
  type: 'Feature',
  geometry: {
    type: 'Point',
    coordinates: [-77.43,18.47]
  },
  properties: {
    title: 'Jamaica, 20 Records',
    description: 'Acropora cervicornis, Acropora palmata, Agaricia lamarcki, Agaricia agaricites, Colpophyllia natans, Diploria strigosa, Dendrogyra cylindrus, Leptoseris cucullata, Madracis decactis, Meandrina meandrites, Montstraea annularis, Montastraea cavernosa, Porites asteroides, Porites porites, Siderastrea siderea, Siderastrea radians, Stephanocoenia intersepta, Eunicea calculata, Plexaurella nutans, Pseudopterogorgia sp.'
  }
},

{
  type: 'Feature',
  geometry: {
    type: 'Point',
    coordinates: [99.99,9.42]
  },
  properties: {
    title: 'Laem Set, 24 Records',
    description: 'Montipora tuberculosa, Acropora millepora, Acropora subulata, Astreopora myriophthalma, Galaxea fascicularis, Pavona frondifera, Pavona decussata, Pavona explanulata, Pachyseis rugosa, Fungia fungites, Turbinaria mesenterina, Symphyllia radians, Favia favus, Favia veroni, Favia pallida, Favia maritima, Favia truncatus, Favites abdita, Favites halicora, Gonistrea pectinata, Platygyra daedalea, Diploastrea heliopora, Porites lutea, Goniopora lobata'
  }
},

{
  type: 'Feature',
  geometry: {
    type: 'Point',
    coordinates: [71.93,-5.86]
  },
  properties: {
    title: 'Chagos Archipelago, 2 Records',
    description: 'Acropora cytherea (2)'
  }
},

{
  type: 'Feature',
  geometry: {
    type: 'Point',
    coordinates: [-60.67,11.238]
  },
  properties: {
    title: 'Trinidad & Tobago, 12 Records',
    description: ' Colpophyllia natans(3), Montastraea cavernosa(3), Montastraea faveolata(3), Siderastrea siderea(3)'
  }
},

{
  type: 'Feature',
  geometry: {
    type: 'Point',
    coordinates: [150.87, -21.75]
  },
  properties: {
    title: 'Southern Great Barrier Reef, 2 Records',
    description: 'Acropora sp.(2)'
  }
},

{
  type: 'Feature',
  geometry: {
    type: 'Point',
    coordinates: [-64.732, 17.770]
  },
  properties: {
    title: 'US Virgin Islands, 1 Record',
    description: 'Acropora palmata'
  }
},

{
  type: 'Feature',
  geometry: {
    type: 'Point',
    coordinates: [109.481, 18.194]
  },
  properties: {
    title: 'Hainan Island, 11 Records',
    description: 'Montipora sp., Goniastrea sp., Platygyra sp., Acropora sp.(2), Leptoria sp., Favia sp., Porites sp., Favites sp., Galaxea sp., Pocillopora sp.'
  }
},

]
};

geojson.features.forEach(function(marker) {

  // create a HTML element for each feature
  var el = document.createElement('div');
  el.className = 'marker';

  // make a marker for each feature and add to the map
  new mapboxgl.Marker(el, { offset: [-30 / 2, -30] })
  .setLngLat(marker.geometry.coordinates)
  new mapboxgl.Marker(el, { offset: [-30 / 2, -30] })
    .setLngLat(marker.geometry.coordinates)
    .setPopup(new mapboxgl.Popup({ offset: 40 }) // add popups
    .setHTML('<h3>' + marker.properties.title + '</h3><p>' + marker.properties.description + '</p>'))
    .addTo(map);
});
</script>

</body>
</html>
