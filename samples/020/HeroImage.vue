<template>
  <div class="heroImage"/>
</template>

<script>
export default {
  name: 'HeroImage',
};

</script>

<style lang="scss" scoped>
.heroImage {
  background-image: url('../assets/planet.jpeg');
  background-repeat: no-repeat;
  background-size: cover;
  width: 100%;
  height: 100vh;
  position: fixed;
  top: 0;
  z-index: -1;
}

.heroImage::after {
  content: "";
  position: absolute;
  background: black;
  opacity: 0.3;
  width: 100%;
  height: 100vh;
  top: 0;
  left: 0;
  z-index: 1;
}
</style>
