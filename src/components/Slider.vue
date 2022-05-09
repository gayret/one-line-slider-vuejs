<script setup>
import { onMounted, reactive } from 'vue'

const slides = reactive([
  {
    id: 0,
    title: 'Title 1',
  },
  {
    id: 1,
    title: 'Title 2',
  },
  {
    id: 2,
    title: 'Title 3',
  },
])

onMounted(() => setInterval(() => slides.unshift(slides.pop()), 2000))
</script>

<template>
  <div class="slider">
    <div class="item" v-for="item in slides" :key="item" :data-slide="item.id">
      {{ item.title }}
    </div>
  </div>
</template>

<style scoped>
.slider {
  display: flex;
  margin: 3em;
}

.slider div:nth-child(2) {
  transform: scale(1.2);
  box-shadow: 0 0 3px #222;
  transition: all 0.1s;
}

.slider .item {
  flex: 1;
  height: 150px;
  display: grid;
  place-items: center;
}

[data-slide='0'] {
  background-color: lightcoral;
}

[data-slide='1'] {
  background-color: limegreen;
}

[data-slide='2'] {
  background-color: lightblue;
}
</style>
