<script setup>
import Sidebar from './components/Sidebar.vue'
import MapOtvaraj from './components/MapOtvaraj.vue'

import { ref } from 'vue'

const sidebar = ref(false)
const opened = ref('')

function showSidebar(clicked) {
  console.log('show', clicked)
  sidebar.value = true
  opened.value = clicked
}

function hideSidebar() {
  sidebar.value = false
  opened.value = ''
}

</script>

<template>
  <div class="content-wrapper">
    <Sidebar v-if="sidebar" v-click-outside="hideSidebar" :show-content-for="opened" />
    <MapOtvaraj @show="showSidebar" />
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
