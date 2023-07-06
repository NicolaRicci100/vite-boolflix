<script>
import axios from 'axios';
import ProductSection from './ProductSection.vue';
import { store } from '../data/store';
export default {
  components: { ProductSection },
  data() {
    return {
      store,
    }
  },
};
</script>

<template>
  <section id="movies">
    <h2>Movies</h2>
    <ProductSection v-for="movie in store.movies" :key="movie.id" :productType="movie" />
  </section>
  <section id="series">
    <h2>Series</h2>
    <ProductSection v-for="serie in store.series" :key="serie.id" :productType="serie" />
  </section>
</template>

<style lang="scss" scoped>
@use '../assets/scss/style.scss';
</style>