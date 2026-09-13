<template>
  <v-app>
   
    <v-main>
      <Navbar/>
      <router-view/>
      <Footer/>
      
    </v-main>
  </v-app>
</template>

<script>
import Navbar from './components/Navbar/Navbar.vue';
import Footer from './components/Footer/Footer.vue';


export default {
    name: "App",
    data: () => ({
    //
    }),
    components: { Navbar, Footer }
}
</script>
<style>
 
</style>
