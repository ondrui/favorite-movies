<template>
  <form @submit.prevent="searchStore.getMovies(SearchMovie)">
    <input
      type="text"
      class="search-input"
      placeholder="Input movie"
      v-model="SearchMovie"
    />
  </form>
  <Loader v-if="searchStore.loader" />
  <div v-else>
    <Movie v-for="movie of searchStore.movies" :key="movie.id" :movie="movie" />
  </div>
</template>

<script setup>
import { ref } from "vue";
import Movie from "./Movie.vue";
import Loader from "./Loader.vue";
import { useSearchStore } from "../stores/searchStore";

const searchStore = useSearchStore();
const SearchMovie = ref("");
</script>

<style scoped>
.search-input {
  border: 1px solid #e7e7e7;
  width: 100%;
  height: 40px;
  padding: 0 10px;
  margin-bottom: 20px;
  border-radius: 10px;
}
</style>
Footer
