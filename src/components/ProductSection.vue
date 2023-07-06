<script>
export default {
  props: {
    productType: Object
  },
  computed: {
    isFlag() {
      const flags = ['it', 'en'];
      return flags.includes(this.productType.original_language);
    },
    srcFlag() {
      const url = new URL(`../assets/img/${this.productType.original_language}.png`, import.meta.url)
      return url.href;
    }
  }
}
</script>

<template>
  <ul>
    <li>{{ productType.title || productType.name }}</li>
    <li>{{ productType.original_title || productType.original_name }}</li>
    <li>
      <img v-if="isFlag" :src="srcFlag" :alt="productType.original_language">
      <span v-else>{{ productType.original_language }}</span>
    </li>
    <li>{{ productType.vote_average }}</li>
  </ul>
</template>

<style lang="scss" scoped>
@use '../assets/scss/style.scss';

img {
  height: 20px;
  width: 30px;
}
</style>