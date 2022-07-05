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

const screenWidth = ref(window.innerWidth)
const desktop = computed(() => screenWidth.value > 992)

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
  iconSize: [220/decreaseBy, 220/decreaseBy]
}))

const vladaIcon = ref(leaflet.icon({
  iconUrl: vladaUrl,
  iconSize: [220/decreaseBy, 220/decreaseBy]
}))
// ---

const checkpoint1 = ref(leaflet.marker([45.81671, 15.97335], {
  icon: checkpoint1Icon.value, 
  zIndexOffset: -10,
  alt: "Policijske stražarnice"
}))
const checkpoint2 = ref(leaflet.marker([45.816675, 15.97398], {
  icon: checkpoint2Icon.value, 
  zIndexOffset: -10,
  alt: "Policijske stražarnice"
}))
const checkpoint3 = ref(leaflet.marker([45.81597, 15.97353], {
  icon: checkpoint3Icon.value, 
  zIndexOffset: -10,
  alt: "Policijske stražarnice"
}))

const fence1 = ref(leaflet.marker([45.81668, 15.973659769227755], {
  icon: fence1Icon.value,
  alt: "Barikade oko Markovog trga"
}))
const fence2 = ref(leaflet.marker([45.81598, 15.97322], {
  icon: fence2Icon.value,
  alt: "Barikade oko Markovog trga"
}))

watch(() => props.walls, (val, prevVal) => {
  if (!val) {

    leaflet.DomUtil.addClass(checkpoint1.value._icon, "leaflet-marker-hidden")
    leaflet.DomUtil.addClass(checkpoint2.value._icon, "leaflet-marker-hidden")
    leaflet.DomUtil.addClass(checkpoint3.value._icon, "leaflet-marker-hidden")
    leaflet.DomUtil.addClass(fence1.value._icon, "leaflet-marker-hidden")
    leaflet.DomUtil.addClass(fence2.value._icon, "leaflet-marker-hidden")

    const mapElement = document.getElementById('map')

    leaflet.DomUtil.addClass(mapElement, "shake")

    setTimeout(() => {
      checkpoint1.value.remove()
      checkpoint2.value.remove()
      checkpoint3.value.remove()

      fence1.value.remove()
      fence2.value.remove()
    }, 2000)
  }
})

onMounted(() => {
  const zoom = desktop.value ? 19 : 18
  const mapCoordinates = desktop.value ? [45.81627, 15.97330] : [45.81640, 15.97365]

  map.value = leaflet.map('map', {
    zoomControl: false
  });

  map.value.setView(mapCoordinates, zoom);

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
  const church = leaflet.marker([45.81637, 15.97365], {
    icon: churchIcon.value,
    alt: "Markov trg s natpisom Otvaraj!"
  }).addTo(map.value);
  church.on('click', churchEvent);

  const parliament = leaflet.marker([45.81632, 15.97438], {
    icon: parliamentIcon.value, 
    alt: "Zgrada Sabora s natpisom Gdje su svi?"
  }).addTo(map.value);
  parliament.on('click', parliamentEvent);

  const vlada = leaflet.marker([45.81642, 15.97291], {
    icon: vladaIcon.value,
    alt: "Zgrada Vlade s natpisom Jel' otvoreno?"
  }).addTo(map.value);
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

<style>
@keyframes shake {
  0% { transform: translate(1px, 1px) rotate(0deg); }
  10% { transform: translate(-1px, -2px) rotate(-1deg); }
  20% { transform: translate(-3px, 0px) rotate(1deg); }
  30% { transform: translate(3px, 2px) rotate(0deg); }
  40% { transform: translate(1px, -1px) rotate(1deg); }
  50% { transform: translate(-1px, 2px) rotate(-1deg); }
  60% { transform: translate(-3px, 1px) rotate(0deg); }
  70% { transform: translate(3px, 1px) rotate(-1deg); }
  80% { transform: translate(-1px, -1px) rotate(1deg); }
  90% { transform: translate(1px, 2px) rotate(0deg); }
  100% { transform: translate(1px, -2px) rotate(-1deg); }
}

#map {
  height: 100vh;
  width: 100%;
  max-width: 100%;
}

#map.shake {
  animation: shake 0.5s; 
  animation-iteration-count: 4;  
}

.leaflet-marker-icon {
  transition: opacity 2s ease-out;
}

.leaflet-marker-hidden {
  opacity: 0;
}
</style>
