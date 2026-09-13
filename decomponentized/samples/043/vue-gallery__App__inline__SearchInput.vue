<template>
  <div :class="[{flexStart: step === 1},'wrapper']">
    <transition name="fade">
      <HeroImage v-if="step === 0"/>
    </transition>
    <Claim v-if="step === 0"/>
    <input
        id="search"
        name="search"
        type="text"
        :class="{ dark: step === 1 }"
        @change="handleInput($event.target.value)"
      />
    <div class="results" v-if="results && !loading && step === 1">
      <Item v-for="item in results" :item="item" :key="item.data[0].nasa_id"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Claim from '@/components/Claim.vue';

import HeroImage from '@/components/HeroImage.vue';
import Item from '@/components/Item.vue';

const API = 'https://images-api.nasa.gov';

export default {
  name: 'App',
  components: { HeroImage, Claim, Item },
  data() {
    return {
      loading: false,
      step: 0,
      results: [],
    };
  },
  methods: {
    handleInput(event) {
      this.loading = true;
      axios.get(`${API}/search?q=${event}&media_type=image`)
        .then((resp) => {
          this.results = resp.data.collection.items;
          this.loading = false;
          this.step = 1;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};

</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600;800&display=swap');

* {
  box-sizing: border-box;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  font-family: 'Montserrat', sans-serif;
  margin: 0;
  padding: 0;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .3s ease;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}

.slide-enter-active, .slide-leave-active {
  transition: margin-top .3s ease;
}

.slide-enter, .slide-leave-to {
  margin-top: -50px;
}

.wrapper {
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 0;
  padding: 30px;
  width: 100%;
  height: 100vh;

  &.flexStart {
    justify-content: flex-start;
  }
}

.results {
  margin-top: 50px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 20px;
  @media (min-width: 768px) {
    grid-template-columns: 1fr 1fr 1fr;
  }
}

input {
  margin-top: 50px;
  display: flex;
  flex-direction: column;
  width: 250px;
  color: white;
  text-align: center;
  font-size: 18px;
  font-weight: 300;
  height: 30px;
  border: 0;
  background: none;
  border-bottom: 1px solid white;
  transition: box-shadow .3s ease-out;
}

input:focus {
  outline: none;
  box-shadow: 0 10px 20px -8px rgba(255, 255, 255, .5);
}

.dark {
  color: #1e3d4a;
  border-bottom-color: #1e3d4a;
}

.dark:focus {
  box-shadow: 0 10px 20px -8px rgba(#1e3d4a, .2);
}
</style>
