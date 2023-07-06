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
  <form @submit.prevent="$emit('form-submit')">
    <input @keyup="$emit('term-change', searchTerm)" v-model.trim="searchTerm" type="text"
      :placeholder="placeholder || 'Scrivi...'">
    <button type="submit">{{ submitLabel || 'Cerca' }}</button>
  </form>
</template>

<style lang="scss" scoped>
@use '../assets/scss/style.scss';
</style>