<script setup>
import { ref, onMounted } from 'vue'

defineProps({
  headerText: String,
  bodyText: String 
})

const hideAccordionBody = ref(true)

</script>

<template>
  <div class="accordion">
    <div class="accordion-header" @click="hideAccordionBody = !hideAccordionBody">
      <h3>{{ headerText }}</h3>
      <div>
        <img alt="open/close arrow" src="../assets/noun-arrow-up.svg" class="arrow-up" :class="{ 'rotate': hideAccordionBody }" />
      </div>
    </div>
    <div class="accordion-body" :class="{ 'hide': hideAccordionBody }">
      <p>{{ bodyText }}</p>
    </div>
  </div>
</template>

<style scoped>
.accordion-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  cursor: pointer;
}

.accordion-header div {
  margin-left: 15px;
}

.accordion-header div img {
  transition: transform 0.5s ease;
}

.accordion-body {
  max-height: 500px;
  overflow: hidden;
  transition: max-height 0.5s ease-out;
}

.hide {
  max-height: 0;
}

.rotate {
  transform: rotate(180deg);
}

.arrow-up {
  width: 42px;
}

h3 {
  font-family: 'Archivo', sans-serif;
  font-weight: 600;
}

p {
  font-weight: 300;
  font-size: 16px;
  line-height: 24px;
  margin-top: 0;
}

hr {
  border-top: #a6a6a6;
  background-color: #a6a6a6;
}

</style>