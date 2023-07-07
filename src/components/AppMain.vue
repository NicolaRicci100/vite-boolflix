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
  <div id="content">
    <section id="movies">
      <h2>Film</h2>
      <ProductSection v-for="movie in store.movies" :key="movie.id" :productType="movie" />
    </section>
    <section id="series">
      <h2>Serie</h2>
      <ProductSection v-for="serie in store.series" :key="serie.id" :productType="serie" />
    </section>
  </div>
</template>

<style lang="scss" scoped>
@use '../assets/scss/style.scss';

#content {
  height: 90vh;
  overflow-y: auto;
  padding: 20px;
}
</style>