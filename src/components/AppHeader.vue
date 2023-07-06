<script>
import SearchBar from './SearchBar.vue'
export default {
  components: { SearchBar },
  data() {
    return {
      titleFilter: ''
    }
  },
  methods: {
    setTitleFilter(term) {
      this.titleFilter = term;
    },
    searchMovie() {
      console.log(this.titleFilter);
    }
  }
};
</script>

<template>
  <nav class="d-flex justify-content-between">
    <h1>Boolflix</h1>
    <SearchBar @term-change="setTitleFilter" @form-submit="searchMovie" />
  </nav>
</template>

<style lang="scss" scoped>
@use '../assets/scss/style.scss';
</style>