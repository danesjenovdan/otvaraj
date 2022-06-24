<script setup>
import Sidebar from './components/Sidebar.vue'
import MapOtvaraj from './components/MapOtvaraj.vue'

import { ref } from 'vue'

const showSidebar = ref(false)

function hideSidebar() {
  showSidebar.value = false
}

</script>

<template>
  <div class="content-wrapper">
    <Sidebar v-if="showSidebar" v-click-outside="hideSidebar" />
    <MapOtvaraj @show="showSidebar = true" />
    <!-- sabor
    vlada
    kucica
    crkva 
    izbor možnosti za akcijo
    -->
  </div>
</template>

<style>
html, body {
  height: 100%;
  width: 100%;
  margin: 0;
  overflow-x: hidden;
}

#app {
  /* font-family: Avenir, Helvetica, Arial, sans-serif; */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
