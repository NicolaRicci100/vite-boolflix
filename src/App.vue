<script>
import AppMain from './components/AppMain.vue'
import AppHeader from './components/AppHeader.vue';
export default {
  components: { AppMain, AppHeader },
}
</script>

<template>
  <AppHeader />
  <AppMain />
</template>

<style lang="scss">
@use './assets/scss/style.scss';
</style>