<script setup>
import { ref } from 'vue';
defineEmits(['getMovies'])

const search = ref('')
</script>

<template>
  <form @submit.prevent="$emit('getMovies', search)" class="flex justify-center items-center gap-2">
    <input v-model="search" placeholder="Batman..." type="text"
      class="outline-none px-3 py-1.5 rounded bg-transparent border-b-2" name="search">
    <button class="bg-transparent rounded ring-2 ring-purple-700 hover:bg-purple-700 px-3 py-1">Search</button>
  </form>
</template>

<style scoped></style>