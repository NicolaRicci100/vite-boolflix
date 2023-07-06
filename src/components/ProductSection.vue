<script>
export default {
  props: {
    productType: Object
  }
}
</script>

<template>
  <ul>
    <li>{{ productType.title || productType.name }}</li>
    <li>{{ productType.original_title || productType.original_name }}</li>
    <li>{{ productType.original_language }}</li>
    <li>{{ productType.vote_average }}</li>
  </ul>
</template>

<style lang="scss" scoped>
@use '../assets/scss/style.scss';
</style>