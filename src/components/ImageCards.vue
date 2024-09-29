<script setup>
import { ref } from 'vue'
import ImageCard from './ImageCard.vue'
import LoadingCard from '@/components/LoadingCard.vue'

defineProps({
  searchLoading: Boolean
})

const cards = ref(
  Array(8)
    .fill()
    .map((_, i) => ({ id: i + 1 }))
)
</script>

<template>
  <div class="imageCardContainer" v-if="searchLoading">
    <LoadingCard v-for="card in cards" :key="card" />
  </div>
  <div class="imageCardContainer" v-if="!searchLoading">
    <ImageCard v-for="card in cards" :key="card" />
  </div>
</template>

<style lang="scss">
.imageCardContainer {
  margin: -40px auto 0 auto;
  width: 70%;
  display: grid;
  grid-gap: 20px;
  grid-column-gap: 40px;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  grid-auto-flow: dense;
  grid-auto-rows: 10px;

  & > * {
    grid-row-end: span 10;
  }

  & > :nth-child(3n) {
    grid-row-end: span 12;
  }

  & > :nth-child(3n -1) {
    grid-row-end: span 14;
  }
}
</style>
