<template>
  <div id="app">
    <h1>Espacios de trabajo</h1>
    <div class="badge-container">
      <div v-for="badge in markers" :key="badge.address">
        <Badge :address="badge.address" :image="badge.image" />
      </div>
    </div>
    <Map v-if="markers.length > 0" :markers="markers" />

  </div>
</template>
<script>
import Badge from './components/badge.vue'
import Map from './components/map.vue'
export default {
  name: 'app',
  data() {
    return {
      markers: []
    }
  },
  components: {
    Badge,
    Map
  },
  mounted() {
    fetch('https://db.enriqueteruel.com/wp-json/markers/v1/post')
      .then((r) => r.json())
      .then((res) => this.markers = res.map(x => x.acf));

  }
}
</script>

<style>
.badge-container {
  padding-top: 60px;
  display: flex;
  justify-content: space-around;
  width: 100%;
  overflow-x: scroll;
  overflow-y: hidden;
}



html,
body {
  margin: 0;
  height: 100%;
  width: 100%;
  background-color: #FAFAFA;
  font-family: 'Roboto', sans-serif;
}


#app>h1 {
  text-align: center;
  color: 212121;
}

#app>h1:hover {
  cursor: pointer;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#footer {
  text-align: center;
  text-decoration: none;
  color: 212121;
}
</style>