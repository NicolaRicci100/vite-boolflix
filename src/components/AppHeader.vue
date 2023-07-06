<script>
import axios from 'axios';
import SearchBar from './SearchBar.vue'
import { store } from '../data/store';
import { api } from '../data/index';
export default {
  components: { SearchBar },
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
</template>

<style lang="scss" scoped>
@use '../assets/scss/style.scss';
</style>