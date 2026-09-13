<template>
<Header v-show="showTemplate" />
  <transition v-if="showTemplate" name="fade">
      <div class="snackbar" role="button" v-show="show" @click="show = false" :class="[color]">
        {{ message }}
      </div>
    </transition>
  <router-view />
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Header from "./components/parts/Header.vue";

export default defineComponent({
  name: 'App',
  components: {
    Header
  },
  data() {
    return {
      showTemplate: true,
      timeout: 3600,
      show: false,
      message: '',
      color: '',
      timeoutId: ''
    }
  },
  created() {
    if (window.location.href.endsWith('/ad')) {
      this.showTemplate = false
    }
    this.$store.subscribe((mutation, state) => {
      if (mutation.type === "snackbar/showMessage") {
        this.message = state.snackbar.content;
        this.color = state.snackbar.color;
        this.show = true;

        this.timeoutId = setTimeout(() => {
          this.close();
        }, this.timeout) as any;
      }
    });
  },
  methods: {
    close() {
      this.show = false;

      if (this.timeoutId) {
        clearTimeout(this.timeoutId as any);
        this.timeoutId = null as any;
      }
    },
  },
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
.snackbar {
  position: fixed;
  bottom: 0;
  width: 100%;
  padding: 20px;
  z-index: 1;
  font-size: x-large;
  border-block: 4px solid black;
  text-align: center;
  cursor: move;
}

.success {
  background: lightgreen;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
