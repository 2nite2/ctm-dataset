<template>
  <MovieCreate />
  <MoviesList />
</template>

<script>
import MovieCreate from '@/components/MovieCreate.vue'
import MoviesList from '@/components/MoviesList.vue'

export default {
  name: 'Home',
  components: { MovieCreate, MoviesList }
}
</script>
