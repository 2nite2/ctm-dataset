<script setup>
import { onBeforeMount, onMounted } from 'vue'
import Jumbor from '@/components/Jumborton.vue'
import CarouselComponent from '@/components/Carounsel.vue'

import { useMovieStore } from '@/stores/index'
const movieStore = useMovieStore()

onBeforeMount(() => {
  movieStore.getCountryFromIP()
})

onMounted(() => {
  movieStore.getUpComingsMovies()
  movieStore.getTopRatedMovies()
  movieStore.getPopularMovies()
})
</script>

<template>
  <main>
    <Jumbor></Jumbor>
    <div class="container">
      <div class="row ps-1 pe-1">
          <h3 class="mt-5 mb-5 mx-2">{{ $t("UpComings") }}</h3>
          <CarouselComponent :data="movieStore.upComingsMovies"></CarouselComponent>
          <h3 class="mt-5 mb-5 mx-2">{{ $t("TopRated") }}</h3>
          <CarouselComponent :data="movieStore.topRatedMovies"></CarouselComponent>
          <h3 class="mt-5 mb-5 mx-2">{{ $t("PopulerMovies") }}</h3>
          <CarouselComponent :data="movieStore.moviesPopular"></CarouselComponent>

        </div>
    </div>
  </main>
</template>
