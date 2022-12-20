<script setup>
import axios from "axios";

const props = defineProps(["id"]);
const emits = defineEmits(["toggleModal"]);

let data = (
  await axios.get(`https://api.themoviedb.org/3/movie/${props.id}`, {
    params: {
      api_key: "26ca7d300d9e397095fa7e1435f5eb3d",
      append_to_response: "videos",
    },
  })
).data;
console.log(data);
</script>

<template>
  <Teleport to="body">
    <div class="modal-outer-container" @click.self="emits('toggleModal')">
      <div class="modal-inner-container">
        <button class="close-button" @click="emits('toggleModal')">X</button>
        <img :src="`http://image.tmdb.org/t/p/w500/${data.poster_path}`" class="poster" />
        <div class="description">
          <h1>{{ data.title }}</h1>
          <p>{{ data.overview }}</p>
          <p>Released in: {{ data.release_date }}</p>
          <p>Runtime: {{ data.runtime }}</p>
          <p>Revenue: {{ data.revenue }}</p>
          <iframe width="360" height="215" class="trailer"
            :src="`https://www.youtube.com/embed/${data.videos.results[0].key}`" frameborder="0"
            allowfullscreeen></iframe>
        </div>
      </div>
    </div>
  </Teleport>
</template>

<style scoped>
.modal-outer-container {
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100vw;
  height: 100vh;
  background: #13192299;
  z-index: 3;
}

.modal-outer-container .modal-inner-container {
  background-color:  rgb(33, 40, 61);
  color: white;
  width: clamp(280px, 100%, 800px);
  height: 450px;
  position: relative;
  display: flex;
}

.modal-outer-container .modal-inner-container .close-button {
  position: absolute;
  right: 0px;
  padding: 1rem;
  border: none;
  background: rgb(33, 40, 61);
  font-weight: bold;
  font-size: 1.25rem;
  color: white;
}
.modal-inner-container>.poster {
  height: 25rem;
  margin: 2rem;
}
.modal-inner-container>.description {
  display: flex;
  flex-wrap: wrap;
}
.modal-inner-container>.description>h1 {
  margin-top: 2rem;
  text-align: center;
}

.modal-inner-container>.description>h3 {
  text-align: center;
  margin-bottom: 1rem;
}
.modal-inner-container>.description>p {
  margin: 5px;
}
</style>
