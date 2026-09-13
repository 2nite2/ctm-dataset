<template>
  <div class="card card-body mt-4">
    <h3>Edit Movies</h3>
    <form @submit.prevent="update">
      <div class="form-group">
        <label>Name</label>
        <input v-model="form.name" class="form-control" required />
      </div>

      <div class="form-group mt-3">
        <label>Email</label>
        <input
          v-model="form.email"
          class="form-control"
          type="email"
          required
        />
      </div>

      <button type="submit" class="btn btn-primary  mt-3">
        Update
      </button>
    </form>
  </div>
</template>

<script>
import { reactive, computed, onMounted } from 'vue'
import { useRoute, useRouter } from 'vue-router'
import { getMovie, updateMovie } from '@/firebase'

export default {
  setup() {
    const router = useRouter()
    const route = useRoute()
    const movieId = computed(() => route.params.id)

    const form = reactive({ name: '', email: '' })
    onMounted(async () => {
      const movie = await getMovie(movieId.value)
      console.log(movie, movieId.value)
      form.name = movie.name
      form.email = movie.email
    })

    const update = async () => {
      await updateMovie(movieId.value, { ...form })
      router.push('/')
      form.name = ''
      form.email = ''
    }

    return { form, update }
  }
}
</script>
