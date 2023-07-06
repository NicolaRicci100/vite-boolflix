<script>
import { api } from './data/index'
import { store } from './data/store'
import { AppHeader } from './components/AppHeader.vue'
export default {
  components: { AppHeader }
}
</script>

<template>
  <AppHeader />
</template>

<style lang="scss">
@use './assets/scss/style.scss';
</style>