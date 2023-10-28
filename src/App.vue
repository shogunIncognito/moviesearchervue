<script setup>
import { ref } from 'vue'
import Movies from './components/Movies.vue'
import Form from './components/Form.vue'

const loading = ref(false)
const moviesState = ref({
  movies: [],
  firstSearch: true
})

const getMovies = async (search) => {
  try {
    loading.value = true
    const res = await fetch(`https://www.omdbapi.com/?s=${search}&apikey=406f0ce1`)
    const json = await res.json()

    moviesState.value.movies = json.Search
    moviesState.value.firstSearch = false
  } catch (error) {
    console.log(error);
  } finally {
    loading.value = false
  }
}
</script>

<template>
  <main class="flex-col w-full flex text-white h-screen">
    <header class="flex justify-center w-full items-center flex-col">
      <h2 class="my-10 text-4xl font-extralight">Movie Searcher</h2>
      <Form @getMovies="getMovies" />
    </header>

    <div v-if="!moviesState.firstSearch && !moviesState.movies" class="my-10 mx-10">
      <h3 class="text-2xl font-bold text-center font-mono">No results</h3>
    </div>
    <div v-else-if="loading"
      class="animate-spin self-center mt-32 rounded-full h-20 w-20 border-t-2 border-b-2 border-purple-700">
    </div>
    <Movies v-else-if="!moviesState.firstSearch" :moviesState="moviesState" />
  </main>
</template>

<style scoped></style>
