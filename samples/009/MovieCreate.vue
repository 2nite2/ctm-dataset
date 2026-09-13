<template>
  <div class="card card-body mt-4">
    <form @submit.prevent="onSubmit">
      <div class="form-group">
        <label>Title</label>
        <input v-model="form.title" class="form-control" required />
      </div>

      <div class="form-group mt-3">
        <label>Year</label>
        <input
          v-model="form.year"
          class="form-control"
          type="text"
          required
        />
      </div>

      <div class="form-group mt-3">
        <label>Category</label>
        <input
          v-model="form.category"
          class="form-control"
          type="text"
          required
        />
      </div>

      <div class="form-group mt-3">
        <label>Cover (url)</label>
        <input
          v-model="form.cover"
          class="form-control"
          type="text"
          required
        />
      </div>

      <button type="submit" class="btn btn-success mt-3">
        Create Movie
      </button>
    </form>
  </div>
</template>

<script>
import { createMovie } from '@/firebase'
import { reactive } from 'vue'

export default {
  setup() {
    const form = reactive({ title: '', year: '', category: '', cover: '' })

    const onSubmit = async () => {
      await createMovie({ ...form })
      form.title = ''
      form.year = ''
      form.category = ''
      form.cover = ''
    }

    return { form, onSubmit }
  }
}
</script>
