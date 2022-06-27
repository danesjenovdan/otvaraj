<script setup>
import { ref, onMounted } from 'vue'

import "leaflet/dist/leaflet.css"
import leaflet from "leaflet"
import imgUrl from '../assets/icons/pin.svg'
import churchUrl from '../assets/icons/cerkev.svg'
import checkpoint1Url from '../assets/icons/checkpoint-levo-zgoraj.svg'
import checkpoint2Url from '../assets/icons/checkpoint-desno-zgoraj.svg'
import checkpoint3Url from '../assets/icons/checkpoint-spodaj.svg'
import fence1Url from '../assets/icons/ograja-zgoraj.svg'
import fence2Url from '../assets/icons/ograja-spodaj.svg'
import parliamentUrl from '../assets/icons/parlament.svg'
import vladaUrl from '../assets/icons/vlada.svg'

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

  // disable moving the map
  map.dragging.disable();

  // add map data
  leaflet.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '© OpenStreetMap',
    maxZoom: 20,
  }).addTo(map);
  // ---

  // create icons
  let churchIcon = leaflet.icon({
    iconUrl: churchUrl,
    iconSize: [220, 220]
  })

  let checkpoint1Icon = leaflet.icon({
    iconUrl: checkpoint1Url,
    iconSize: [60, 60]
  })

  let checkpoint2Icon = leaflet.icon({
    iconUrl: checkpoint2Url,
    iconSize: [60, 60]
  })

  let checkpoint3Icon = leaflet.icon({
    iconUrl: checkpoint3Url,
    iconSize: [60, 60]
  })
  
  let fence1Icon = leaflet.icon({
    iconUrl: fence1Url,
    iconSize: [350, 100]
  })

  let fence2Icon = leaflet.icon({
    iconUrl: fence2Url,
    iconSize: [550, 200]
  })

  let parliamentIcon = leaflet.icon({
    iconUrl: parliamentUrl,
    iconSize: [190, 190]
  })

  let vladaIcon = leaflet.icon({
    iconUrl: vladaUrl,
    iconSize: [200, 150]
  })
  // ---

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

  // add icons to map
  const church = leaflet.marker([45.8164, 15.973645607777067], {icon: churchIcon}).addTo(map);
  church.on('click', log);

  const parliament = leaflet.marker([45.81632, 15.97438], {icon: parliamentIcon}).addTo(map);
  church.on('click', log);

  const vlada = leaflet.marker([45.81637, 15.97296], {icon: vladaIcon}).addTo(map);
  church.on('click', log);

  const fence1 = leaflet.marker([45.81668, 15.973659769227755], {icon: fence1Icon}).addTo(map);
  church.on('click', log);

  const fence2 = leaflet.marker([45.81598, 15.97322], {icon: fence2Icon}).addTo(map);
  church.on('click', log);

  const checkpoint1 = leaflet.marker([45.81671, 15.97335], {icon: checkpoint1Icon, zIndexOffset: -10}).addTo(map);
  church.on('click', log);

  const checkpoint2 = leaflet.marker([45.816675, 15.97398], {icon: checkpoint2Icon, zIndexOffset: -10}).addTo(map);
  church.on('click', log);

  const checkpoint3 = leaflet.marker([45.81597, 15.97353], {icon: checkpoint3Icon, zIndexOffset: -10}).addTo(map);
  church.on('click', log);

  // vlada
  const latlngs1 = [[45.816717, 15.972668], [45.81666, 15.97333], [45.81602, 15.97323], [45.81607, 15.97252]];
  const vladaPoly = leaflet.polygon(latlngs1, {color: 'red'}).addTo(map);
  vladaPoly.on('click', log);

  // sabor
  const latlngs2 = [[45.81663, 15.97405], [45.81662, 15.97481], [45.81585, 15.97475], [45.81594, 15.97393]];
  leaflet.polygon(latlngs2, {color: 'blue'}).addTo(map);


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
