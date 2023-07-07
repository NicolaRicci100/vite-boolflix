<script>
import axios from 'axios';
import { poster } from '../data/index';
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
    },
    posterPath() {
      if (!this.productType.poster_path) return poster.placeholder;
      return poster.prefix + this.productType.poster_path;
    },
    vote() {
      return Math.ceil(this.productType.vote_average / 2);
    }
  },
  methods: {
    starVote(n) {
      return n <= this.vote ? 'fas' : 'far';
    }
  }
}
</script>

<template>
  <!-- <ul>
    <li>{{ productType.title || productType.name }}</li>
    <li>{{ productType.original_title || productType.original_name }}</li>
    <li class="flag">
      <img v-if="isFlag" :src="srcFlag" :alt="productType.original_language">
      <span v-else>{{ productType.original_language }}</span>
    </li>
    <li>
      <i v-for="n in 5" :key="n" :class="starVote(n)" class="fa-star"></i>
    </li>
    <li class="poster"><img :src="posterPath" :alt="productType.title || productType.name"></li>
  </ul> -->


  <figure class="poster">
    <img :src="posterPath" :alt="productType.title || productType.name">
    <div class="description">
      <h4>{{ productType.title || productType.name }}</h4>
      <div>{{ productType.original_title || productType.original_name }}</div>
      <div class="flag">
        <img v-if="isFlag" :src="srcFlag" :alt="productType.original_language">
        <span v-else>{{ productType.original_language }}</span>
      </div>
      <div>
        <i v-for="n in 5" :key="n" :class="starVote(n)" class="fa-star"></i>
      </div>
    </div>
  </figure>
</template>

<style lang="scss" scoped>
@use '../assets/scss/style.scss';

.description {

  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  opacity: 0;

}

.poster {
  height: 400px;
  width: 300px;
  margin: 10px 10px;
  position: relative;

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
    object-position: 50% 0;
    transition: .5s ease;
  }
}

.poster:hover>img {
  opacity: 0.4;
}

.poster:hover .description {
  opacity: 1;
  transition: .5s ease;
}
</style>