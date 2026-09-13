<template>
  <div class="font-poppins">
    <Header />
    <div class="p-2">
      <Form />
      <Search />
      <Bookshelf />
    </div>
    <div class="p-3 m-3 text-center">
        <p class="mb-2">Simple Bookshelf App by ryuuwiz</p>
        <p class="mb-2">Version {{ version }}</p>
        <a href="https://github.com/ryuuwiz" target="_blank">
          <i class="fab fa-github-alt fa-2x cursor-pointer"></i>
        </a>
      </div>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Form from './components/Form.vue'
import Search from './components/Search.vue'
import Bookshelf from './components/Bookshelf.vue'
import { version } from '../package.json'


export default {
  name: 'App',
  components: { Header, Form, Bookshelf, Search },
  setup() {
    return { version }
  },
}
</script>
