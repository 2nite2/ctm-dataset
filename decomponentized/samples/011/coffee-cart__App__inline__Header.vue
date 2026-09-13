<template>
  <ul v-show="showTemplate">
      <li>
        <router-link aria-label="Menu page" to="/">menu</router-link>
      </li>
      <li>
        <router-link aria-label="Cart page" to="/cart">cart ({{ cartCount }})</router-link>
      </li>
      <li>
        <router-link aria-label="GitHub page" to="/github">github</router-link>
      </li>
    </ul>
  <Snackbar v-show="showTemplate" />
  <router-view />
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import { mapGetters } from 'vuex';

import Snackbar from "./components/parts/Snackbar.vue";

export default defineComponent({
  name: 'App',
  components: {
    Snackbar
  },
  computed: {
    ...mapGetters({
      cartCount: "cart/cartCount"
    })
  },
  data() {
    return {
      showTemplate: true
    }
  },
  created() {
    if (window.location.href.endsWith('/ad')) {
      this.showTemplate = false
    }
  }
})
</script>

<style>
body {
  font-size: 18px;
  background: rgb(224, 255, 255, 0.15);
  font-family: 'Lobster', Times;
}
</style>

<style scoped>
ul {
  display: flex;
  justify-content: center;
  border-bottom: 4px solid black;
  padding: 0;
  position: sticky;
  top: 0;
  z-index: 1;
  background: rgb(250, 255, 255);
  margin-block: 0;
}

li {
  list-style: none;
  padding: 10px 10px;
}

a {
  color: black;
  font-weight: bold;
  text-decoration: none;
}

a:hover {
  color: grey;
  text-decoration: none;
  border-bottom: 1px dotted grey;
}

a.router-link-active {
  color: goldenrod;
  border-bottom: 1px dotted goldenrod;
}

@media (min-width: 500px) {
  li {
    padding: 10px 20px;
  }

  a {
    font-size: 1.2rem;
  }
}
</style>
