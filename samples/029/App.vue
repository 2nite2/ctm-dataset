<template>
  <div class="font-poppins">
    <Header />
    <div class="p-2">
      <Form />
      <Search />
      <Bookshelf />
    </div>
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Form from './components/Form.vue'
import Search from './components/Search.vue'
import Bookshelf from './components/Bookshelf.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Header,
    Form,
    Bookshelf,
    Search,
    Footer,
  },
}
</script>
