<script setup>
import Sidebar from './components/Sidebar.vue'
import MapOtvaraj from './components/MapOtvaraj.vue'

import { ref } from 'vue'

const sidebar = ref(false)
const walls = ref(true)
const opened = ref('')

function showSidebar(clicked) {
  sidebar.value = true
  opened.value = clicked
}

function hideSidebar() {
  sidebar.value = false
  opened.value = ''
}

function hideWalls() {
  walls.value = false
}

</script>

<template>
  <div class="content-wrapper">
    <Sidebar 
      v-click-outside="hideSidebar" 
      :show="sidebar" 
      :show-content-for="opened" 
      @hide="hideSidebar"
      @hide-walls="hideWalls"
    />
    <MapOtvaraj
      :walls="walls"
      @show="showSidebar" 
    />
  </div>
</template>

<style>
html, body {
  height: 100%;
  width: 100%;
  margin: 0;
  overflow: hidden;
}

#app {
  font-family: 'Roboto', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  overflow: hidden;
}
</style>
