<template>
  <l-map :zoom="10" :center="initialLocation">
    <l-tile-layer url="http://{s}.tile.osm.org/{z}/{x}/{y}.png"></v-tilelayer>
    <l-locate-control/>
  </l-map>
</template>

<script>
import { LMap, LTileLayer } from "vue2-leaflet";
import LLocateControl from './Vue2LeafletLocatecontrol';

export default {
  components: {
    LMap,
    LTileLayer,
    LLocateControl
  },

  data() {
    return {
      initialLocation: [59.93428, 30.335098]
    }
  }
}
</script>

<style>
@import "~leaflet/dist/leaflet.css";
@import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css";
html,
body {
  height: 100%;
  margin: 0;
}
</style>
