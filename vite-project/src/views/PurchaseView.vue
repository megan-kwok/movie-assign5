<script setup>
import axios from "axios";
import { ref } from 'vue';

import SiteModal from '../components/SiteModal.vue';
import SiteHeader from '../components/SiteHeader.vue';
import SiteFooter from '../components/SiteFooter.vue';

const showModal = ref(false);
const selectedId = ref(0);

const openModal = (id) => {
  showModal.value = true;
  selectedId.value = id;
}

const closeModal = () => {
  showModal.value = false;
}

let data = (await axios.get("https://api.themoviedb.org/3/trending/movie/day", {
  params: {
    api_key: "26ca7d300d9e397095fa7e1435f5eb3d",
  }
})).data.results;
console.log(data);
</script>

<template>
  <SiteHeader />
  <div class="posters-container">
    <img v-for="movie in data" @click="openModal(movie.id)" class="posters"
      :src="`http://image.tmdb.org/t/p/w500/${movie.poster_path}`" />
    <SiteModal v-if="showModal" @toggleModal="closeModal()" :id="selectedId" />
    </div>
  <SiteFooter />
</template>

<style scoped>
.posters-container {
  display: flex;
  flex-wrap: wrap;
}
.posters {
  height: 25rem;
  padding: 1rem;
  margin: 1rem;
}
</style>
