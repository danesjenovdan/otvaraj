<script setup>
import { ref, watch, onMounted, computed } from 'vue'

import "leaflet/dist/leaflet.css"
import leaflet from "leaflet"
import churchUrl from '../assets/icons/cerkev.svg'
import checkpoint1Url from '../assets/icons/checkpoint-levo-zgoraj.svg'
import checkpoint2Url from '../assets/icons/checkpoint-desno-zgoraj.svg'
import checkpoint3Url from '../assets/icons/checkpoint-spodaj.svg'
import fence1Url from '../assets/icons/ograja-zgoraj.svg'
import fence2Url from '../assets/icons/ograja-spodaj.svg'
import parliamentUrl from '../assets/icons/parlament.svg'
import vladaUrl from '../assets/icons/vlada.svg'

const props = defineProps({
  walls: Boolean,
})

const emit = defineEmits(['show'])

const screenWidth = ref(window.innerWidth);
const desktop = computed(() => screenWidth.value > 992);

// events
function churchEvent() {
  emit('show', 'church')
}

function parliamentEvent() {
  emit('show', 'parliament')
}

function governmentEvent() {
  emit('show', 'government')
}

function policeEvent() {
  emit('show', 'police')
}

const zoom = desktop.value ? 19 : 18

const map = ref()

const decreaseBy = desktop.value ? 1 : 2

// create icons
const churchIcon = ref(leaflet.icon({
  iconUrl: churchUrl,
  iconSize: [220/decreaseBy, 220/decreaseBy]
}))

const checkpoint1Icon = ref(leaflet.icon({
  iconUrl: checkpoint1Url,
  iconSize: [60/decreaseBy, 60/decreaseBy]
}))

const checkpoint2Icon = ref(leaflet.icon({
  iconUrl: checkpoint2Url,
  iconSize: [60/decreaseBy, 60/decreaseBy]
}))

const checkpoint3Icon = ref(leaflet.icon({
  iconUrl: checkpoint3Url,
  iconSize: [60/decreaseBy, 60/decreaseBy]
}))

const fence1Icon = ref(leaflet.icon({
  iconUrl: fence1Url,
  iconSize: [350/decreaseBy, 100/decreaseBy]
}))

const fence2Icon = ref(leaflet.icon({
  iconUrl: fence2Url,
  iconSize: [550/decreaseBy, 200/decreaseBy]
}))

const parliamentIcon = ref(leaflet.icon({
  iconUrl: parliamentUrl,
  iconSize: [190/decreaseBy, 190/decreaseBy]
}))

const vladaIcon = ref(leaflet.icon({
  iconUrl: vladaUrl,
  iconSize: [200/decreaseBy, 150/decreaseBy]
}))
// ---

const checkpoint1 = ref(leaflet.marker([45.81671, 15.97335], {icon: checkpoint1Icon.value, zIndexOffset: -10}));
const checkpoint2 = ref(leaflet.marker([45.816675, 15.97398], {icon: checkpoint2Icon.value, zIndexOffset: -10}));
const checkpoint3 = ref(leaflet.marker([45.81597, 15.97353], {icon: checkpoint3Icon.value, zIndexOffset: -10}));

const fence1 = ref(leaflet.marker([45.81668, 15.973659769227755], {icon: fence1Icon.value}));
const fence2 = ref(leaflet.marker([45.81598, 15.97322], {icon: fence2Icon.value}));

watch(() => props.walls, (val, prevVal) => {
  if (!val) {
    checkpoint1.value.remove();
    checkpoint2.value.remove();
    checkpoint3.value.remove();

    fence1.value.remove();
    fence2.value.remove();
  }
})

onMounted(() => {
  const zoom = desktop.value ? 19 : 18

  map.value = leaflet.map('map', {
    zoomControl: false
  });

  map.value.setView([45.816272, 15.973636], zoom);

  // disable moving the map
  map.value.dragging.disable();
  map.value.doubleClickZoom.disable();
  map.value.touchZoom.disable();
  map.value.scrollWheelZoom.disable();
  map.value.boxZoom.disable();
  map.value.keyboard.disable();
  if (map.value.tap) map.value.tap.disable();

  // add map data
  leaflet.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '© OpenStreetMap',
    maxZoom: 20,
  }).addTo(map.value);
  // ---


  // add icons to map
  const church = leaflet.marker([45.8164, 15.973645607777067], {icon: churchIcon.value}).addTo(map.value);
  // church.bindTooltip("Otvaraj!", { direction: 'bottom', offset: [0, 120] }).openTooltip();
  church.on('click', churchEvent);

  const parliament = leaflet.marker([45.81632, 15.97438], {icon: parliamentIcon.value}).addTo(map.value);
  // parliament.bindTooltip("Što i koliko radi tvoja zastupnik_ca?").openTooltip();
  parliament.on('click', parliamentEvent);

  const vlada = leaflet.marker([45.81637, 15.97296], {icon: vladaIcon.value}).addTo(map.value);
  // vlada.bindTooltip("Jel’ otvoreno?").openTooltip();
  vlada.on('click', governmentEvent);

  fence1.value.addTo(map.value);
  fence1.value.on('click', policeEvent);

  fence2.value.addTo(map.value);
  fence2.value.on('click', policeEvent);

  checkpoint1.value.addTo(map.value);
  checkpoint1.value.on('click', policeEvent);

  checkpoint2.value.addTo(map.value);
  checkpoint2.value.on('click', policeEvent);

  checkpoint3.value.addTo(map.value);
  checkpoint3.value.on('click', policeEvent);

  const latlngs1 = [[45.816717, 15.972668], [45.81666, 15.97333], [45.81602, 15.97323], [45.81607, 15.97252]];
  const vladaPoly = leaflet.polygon(latlngs1, {color: '#258498'}).addTo(map.value);
  vladaPoly.on('click', governmentEvent);

  const latlngs2 = [[45.81663, 15.97405], [45.81662, 15.97481], [45.81585, 15.97475], [45.81594, 15.97393]];
  const parliamentPoly = leaflet.polygon(latlngs2, {color: '#258498'}).addTo(map.value);
  parliamentPoly.on('click', parliamentEvent);

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
