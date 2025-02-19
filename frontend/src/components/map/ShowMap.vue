<template>
  <div id="map"></div>
</template>

<script>
import L from 'leaflet'
import 'leaflet/dist/leaflet.css'

export default {
  name: 'ShowMap',
  mounted() {
    this.initMap()
  },
  methods: {
    initMap() {
      // Initialize the map and set its view to a specific geographical coordinates and zoom level
      const map = L.map('map').setView([7.28928, 125.69029], 13)

      // Add a tile layer (you can use different tile layers like OpenStreetMap, Mapbox, etc.)
      L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        attribution: '© OpenStreetMap contributors',
      }).addTo(map)
    },
  },
}
</script>

<style scoped>
#map {
  height: 98%; /* Set the height of the map */
  width: 100%; /* Set the width of the map */
}
</style>
