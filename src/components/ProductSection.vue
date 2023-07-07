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
    <div class="description p-3">
      <h4>{{ productType.title || productType.name }}</h4>
      <div>{{ productType.original_title || productType.original_name }}</div>
      <div class="flag py-2 d-flex align-items-center">
        <span class="me-2">Lingua: </span>
        <img v-if="isFlag" :src="srcFlag" :alt="productType.original_language">
        <span v-else>{{ productType.original_language }}</span>
      </div>
      <div>
        <span>Voto: </span>
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
  width: 100%;
  height: 100%;
}

.poster {
  height: 450px;
  width: 300px;
  margin: 10px 20px;
  position: relative;
  cursor: pointer;

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
    transition: .5s ease;
  }
}

.poster:hover>img {
  opacity: 0.2;
}

.poster:hover .description {
  opacity: 1;
  transition: .5s ease;
}

.flag {
  width: 30px;
}
</style>