<template>
  <div class="font-poppins">
    <header
        class="p-4 mb-5 shadow-xl bg-gradient-to-r from-indigo-400 to-blue-500"
      >
        <h1 class="text-3xl text-center font-bold text-white">
          <i class="fas fa-book fa-lg mr-2"></i> Bookshelf App
        </h1>
      </header>
    <div class="p-2">
      <Form />
      <Search />
      <Bookshelf />
    </div>
    <Footer />
  </div>
</template>

<script>

import Form from './components/Form.vue'
import Search from './components/Search.vue'
import Bookshelf from './components/Bookshelf.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: { Form, Bookshelf, Search, Footer },
}
</script>
