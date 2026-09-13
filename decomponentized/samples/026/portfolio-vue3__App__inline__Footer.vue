<template>
  <v-app>
   
    <v-main>
      <Navbar/>
      <router-view/>
      <v-footer
           dark
           padless
         >
           <v-card
             flat
             tile
             class="pink white--text text-center"
             style="{background: black}"
           >
             <v-card-text>
               <v-btn
                 v-for="icon in icons"
                 :key="icon"
                 class="mx-4 white--text"
                 icon
               >
                 <v-icon size="24px">
                   {{ icon }}
                 </v-icon>
               </v-btn>
             </v-card-text>
 
             <v-card-text class="white--text pt-0">
       Nulla placerat augue vel ipsum ultrices, cursus iaculis dui sollicitudin. Vestibulum eu ipsum vel diam elementum tempor vel ut orci. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.
             </v-card-text>
 
             <v-divider></v-divider>
 
             <v-card-text class="white--text">
               {{ new Date().getFullYear() }} — <strong>Fouzia B.</strong>
             </v-card-text>
           </v-card>
         </v-footer>
      
    </v-main>
  </v-app>
</template>

<script>
import Navbar from './components/Navbar/Navbar.vue';



export default {
    name: "App",
    data: () => ({
      icons: [
        'mdi-facebook',
        'mdi-github',
        'mdi-linkedin',
        'mdi-instagram',
      ],
    }),
    components: { Navbar }
}
</script>
<style>
 
</style>
