<template>
  <div>
    <div id='map' class='map'> </div>
  </div>
</template>
    
<script>

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Map',
  mounted() {

    window.mapboxgl.accessToken = 'pk.eyJ1IjoiZW5yaXF1ZXRlcnUiLCJhIjoiY2w0YjQ3NjJwMGx4cjNobzdtamZkaHk4OCJ9.rGcxNb8EiJDHcsknpc1n_A';
    var map = new window.mapboxgl.Map({
      container: 'map',
      style: 'mapbox://styles/mapbox/dark-v10',
      center: [-3.70256, 40.4165],
      zoom: 5

    });


    map.on('load', (() => {

      this.markers.forEach(function (marker) {
        var el = document.createElement('div');
        el.className = 'marker';

        new window.mapboxgl.Marker(el)
          .setLngLat([parseFloat(marker.longitude), parseFloat(marker.latitude)])
          .addTo(map);
      });

      this.markers.forEach((x) => {
        document.getElementById(x.address)
          .addEventListener('click', () => {
            map.flyTo({
              center: [parseFloat(x.longitude), parseFloat(x.latitude)],
              zoom: 15
            })
              ;
          }
          )
      })

    }).bind(this));
  },
  props: {
    markers: Array
  }
}
</script>
    
<style>
.marker {
  background-image: url('./../assets/mapbox-icon.png');
  background-size: cover;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  cursor: pointer;
}

.map {
  height: 500px;
  border: #f6e767 3px solid;
  border-radius: 7px;
}
</style>