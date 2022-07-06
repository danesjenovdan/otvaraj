<script setup>
import Sidebar from './components/Sidebar.vue'
import MapOtvaraj from './components/MapOtvaraj.vue'
import WelcomeText from './components/WelcomeText.vue';
import MailSabor from './components/MailSabor.vue';
import MailVlada from './components/MailVlada.vue';

import { ref } from 'vue'

const sidebar = ref(false)
const walls = ref(true)
const opened = ref('')
const showMailSabor = ref(false)
const showMailVlada = ref(false)

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

function hideMailSabor() {
  showMailSabor.value = false
}

function hideMailVlada() {
  showMailVlada.value = false
}

</script>

<template>
  <div class="content-wrapper">
    <WelcomeText />
    <MailSabor :show="showMailSabor" v-click-outside="hideMailSabor" />
    <MailVlada :show="showMailVlada" v-click-outside="hideMailVlada" />
    <Sidebar 
      v-click-outside="hideSidebar" 
      :show="sidebar" 
      :show-content-for="opened" 
      @hide="hideSidebar"
      @hide-walls="hideWalls"
      @show-mail-sabor="showMailSabor = true"
      @show-mail-vlada="showMailVlada = true"
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
