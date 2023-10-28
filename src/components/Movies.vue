<script setup>
defineProps(['moviesState'])
</script>

<template>
    <section class="my-10 mx-10">
      <h3 class="text-2xl font-bold text-center">Results: {{ moviesState.movies.length }}</h3>
      <ul class="grid gap-5 w-full grid-cols-1 md:grid-cols-2 lg:grid-cols-6 grid-res my-10">
        <li v-for="movie in moviesState.movies" :key="movie.imdbID">
          <article class="relative bg-neutral-600 h-full rounded">
            <div class="z-50 absolute w-full h-full px-5 py-2 bg-black/60">
              <span class="top-1.5 px-1 bg-red-800 rounded p-0.5 capitalize right-1.5 absolute">{{ movie.Type }}</span>
              <h4 class="text-2xl pt-6 font-bold">{{ movie.Title }}</h4>
              <p>{{ movie.Year }}</p>
            </div>
            <img class="object-cover rounded top-0 w-full h-full" :src="movie.Poster" :alt="movie.Title">
          </article>
        </li>
      </ul>
    </section>
</template>

<style scoped>

</style>