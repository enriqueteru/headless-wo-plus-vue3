 <template>
  <div id="app">
    <div class="badge-container">
      <div v-for="badge in markers" :key="badge.address">
        <Badge :name="badge.address" :image="badge.image" />
      </div>
    </div>
    <Map v-if="markers.length > 0" :markers="markers" />
        
  </div>
</template>
<script>
export default {
  name: 'app',
  data(){
    return {
      markers: []
    }
  },
  mounted(){
    fetch('https://db.enriqueteruel.com/wp-json/markers/v1/post')
      .then((r) => r.json())
      .then((res) => this.markers = res.map(x => x.acf))
      .then(r => console.log(r));
  }
}
</script>