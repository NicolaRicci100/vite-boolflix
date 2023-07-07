<script>
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
    <h2>Film</h2>
    <section id="movies" class="d-flex flex-wrap justify-content-start">
      <ProductSection v-for="movie in store.movies" :key="movie.id" :productType="movie" />
    </section>
    <h2>Serie</h2>
    <section id="series" class="d-flex flex-wrap justify-content-start">
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
  background-color: lightgray;
}
</style>