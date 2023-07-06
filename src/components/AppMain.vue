<script>
import axios from 'axios';
import SearchBar from './SearchBar.vue'
import ProductSection from './ProductSection.vue';
import { store } from '../data/store';
import { api } from '../data/index';
export default {
  components: { SearchBar, ProductSection },
  data() {
    return {
      store,
      titleFilter: ''
    }
  },
  methods: {
    setTitleFilter(term) {
      this.titleFilter = term;
    },
    searchProduct() {
      console.log(this.titleFilter);
      if (!this.titleFilter) {
        store.movies = [];
        store.series = [];
        return;
      };
      const { key, language, baseUri } = api;
      const axiosParams = {
        params: {
          api_key: key,
          language,
          query: this.titleFilter
        }
      }
      axios.get(`${baseUri}/search/movie`, axiosParams).then(res => {
        store.movies = res.data.results;
      });
      axios.get(`${baseUri}/search/tv`, axiosParams).then(res => {
        store.series = res.data.results;
      })
    }
  }
};
</script>

<template>
  <nav class="d-flex justify-content-between">
    <h1>Boolflix</h1>
    <SearchBar @term-change="setTitleFilter" @form-submit="searchProduct" />
  </nav>
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