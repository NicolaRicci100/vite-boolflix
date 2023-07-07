<script>
export default {
  data() {
    return {
      searchTerm: ''
    }
  },
  props: {
    placeholder: String,
    submitLabel: String
  },
  emits: ['term-change', 'form-submit']
}
</script>

<template>
  <form class="d-flex align-items-center justify-content-center" @submit.prevent="$emit('form-submit')">
    <input class="rounded-start" type="text" @keyup="$emit('term-change', searchTerm)" v-model.trim="searchTerm"
      :placeholder="placeholder || 'Scrivi...'">
    <button class="btn btn-danger rounded-0 rounded-end" type="submit">{{ submitLabel || 'Cerca' }}</button>
  </form>
</template>

<style lang="scss" scoped>
@use '../assets/scss/style.scss';

input,
button {
  height: 40px;
  border: 2px solid transparent;
  outline-color: #dc3545;
}
</style>