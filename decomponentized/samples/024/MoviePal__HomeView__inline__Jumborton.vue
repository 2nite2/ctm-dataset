<script setup>
import { onBeforeMount } from 'vue'

import Home from '@/components/Home.vue'
import { useMovieStore } from '@/stores/index'
const movieStore = useMovieStore()

onBeforeMount(() => {
  movieStore.getCountryFromIP()
})

</script>

<template>
  <main>
    <div class="container mt-1 pt-5 text-center rounded-3">
        <div class="row py-2 rounded-3">
          <h1 class="fst-italic text-detail">Movie Pal</h1>
          <p class="mb-2 font-monospace text-detail">{{ $t("Discover") }}</p>
        </div>
      </div>
    <div class="container">
      <Home></Home>
    </div>
  </main>
</template>


<style scoped>
.row {
  background-image: url("../assets/jumbortonimage.jpg");
}

.text-detail {
  color: silver;
}
</style>
