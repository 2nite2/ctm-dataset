<template>
  <div class="card mt-4">
    <table class="table m-0">
      <thead>
        <tr>
          <th scope="col">Title</th>
          <th scope="col">Year</th>
          <th scope="col">Category</th>
          <th scope="col">Cover</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="{ id, title, year, category, cover } in movies" :key="id">
          <td>{{ title }}</td>
          <td>{{ year }}</td>
          <td>{{ category }}</td>
          <td>{{ cover }}</td>
          <td>
            <router-link :to="`/edit/${id}`">
              <button class="btn btn-primary btn-sm me-2">
                Edit
              </button>
            </router-link>
            <button class="btn btn-danger btn-sm" @click="deleteMovie(id)">
              Delete
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { useLoadMovies, deleteMovie } from '@/firebase'

export default {
  setup() {
    const movies = useLoadMovies()
    return { movies, deleteMovie }
  }
}
</script>
