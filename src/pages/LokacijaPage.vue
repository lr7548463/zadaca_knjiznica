<template>
  <q-page class="q-pa-lg">
    <h1 class="text-h4"> Lokacija knjižnice </h1>

    <p class="text-body1"> Na karti možete pogledati područje grada Rijeke. </p>

    <div id="map" style="height: 500px; width: 100%"></div>
  </q-page>
</template>

<script setup>
import { onMounted, onBeforeUnmount } from 'vue'
import * as L from 'leaflet'
import 'leaflet/dist/leaflet.css'

let initialMap = null

onMounted(() => {
  initialMap = L.map('map').setView([45.3312, 14.4322], 13)

  L.tileLayer('https://a.tile.openstreetmap.fr/hot/{z}/{x}/{y}.png', {
    maxZoom: 19,
    attribution:
      '&copy; OpenStreetMap contributors, Tiles style by Humanitarian OpenStreetMap Team'
  }).addTo(initialMap)

  L.circleMarker([45.3312, 14.4322], {
    radius: 8,
    color: 'red',
    fillColor: 'red',
    fillOpacity: 0.7
  })
    .addTo(initialMap)
    .bindPopup('Lokacija na području Rijeke')
})

onBeforeUnmount(() => {
  if (initialMap) {
    initialMap.remove()
  }
})
</script>
