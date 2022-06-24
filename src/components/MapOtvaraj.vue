<script setup>
import { ref, onMounted } from 'vue'

import "leaflet/dist/leaflet.css"
import leaflet from "leaflet"
import imgUrl from '../assets/icons/pin.svg'

const showChurch = ref(false)

const emit = defineEmits(['show'])

// defineProps({
//   msg: String
// })

function log() {
  emit('show')
}

let map;




onMounted(() => {
  map = leaflet.map('map', {
    zoomControl: false,
    scrollWheelZoom: false
  }).setView([45.816272, 15.973636], 19);

  map.dragging.disable();

  leaflet.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '© OpenStreetMap',
    maxZoom: 20,
  }).addTo(map);

  let mapIcon = leaflet.icon({
    iconUrl: imgUrl,
    iconSize: [60, 60]
  })

  // icon
//   var icon = L.icon({
//     iconUrl: 'leaf-green.png',
//     shadowUrl: 'leaf-shadow.png',

//     iconSize:     [38, 95], // size of the icon
//     shadowSize:   [50, 64], // size of the shadow
//     iconAnchor:   [22, 94], // point of the icon which will correspond to marker's location
//     shadowAnchor: [4, 62],  // the same for the shadow
//     popupAnchor:  [-3, -76] // point from which the popup should open relative to the iconAnchor
// });

  // church
  const crkva = leaflet.marker([45.816426862740336, 15.973645607777067], {icon: mapIcon}).addTo(map);
  crkva.on('click', log);

  // parliament
  const latlngs1 = [[45.816717, 15.972668],[45.81665448099697, 15.973320536207437],[45.81601521042152, 15.973196831357253],[45.81607619378649, 15.97250287731962]];
  const vlada = leaflet.polygon(latlngs1, {color: 'red'}).addTo(map);
  vlada.on('click', log);

  // sabor
  const latlngs2 = [[45.81666289240078, 15.97411104033098],[45.81661032109227, 15.974738616156317],[45.81596053562144, 15.974642066028593],[45.815987873027055, 15.973970740926973]];
  leaflet.polygon(latlngs2, {color: 'blue'}).addTo(map);

  // policija
  leaflet.circle([45.8167049494219, 15.973335622144996], {color: 'black', radius: 5}).addTo(map);
  leaflet.circle([45.81665027529974, 15.974076342636806], {color: 'black', radius: 5}).addTo(map);
  leaflet.circle([45.815977724108635, 15.973511212700387], {color: 'black', radius: 5}).addTo(map);

});

</script>

<template>
  <div id="map"></div>

</template>

<style scoped>
#map {
  height: 100vh;
  width: 100%;
  max-width: 100%;
}
</style>
