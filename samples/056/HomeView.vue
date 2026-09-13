<template>
  <v-app :style="{ background: $vuetify.theme.themes.dark.background }">
   
    <v-container fluid>
      <div class="head">
        <v-row>
          <v-col cols="5">
            <div style="position: relative" class="mt-16">
              <h1 class="text-white">Hello,</h1>
              <h1>I'm Fouzia BENADIDA</h1>
              <span class="text-grey">Frontend developer</span><br />
              <v-btn tile dark class="text-yellow mt-8" variant="outlined">
                Contact me
              </v-btn>
            </div>
          </v-col>
          <v-col cols="2">
            <div
              style="
                position: absolute;
                z-index: 9999;
                bottom: 0;
                margin-left: auto;
                margin-right: auto;
                left: 0;
                right: 0;
                text-align: center;
              "
              class="mt-16"
            >
              <i class="fa fa-angle-double-down" aria-hidden="true"></i>
            </div>
          </v-col>
          <v-col cols="5">
            <div style=" position:absolute, z-index: 9999; " class="mt-16">
              <v-img
                class="photo-fouzia"
                src="../assets/fouzia.jpg"
                contain
                max-height="300"
              ></v-img>
            </div>
          </v-col>
        </v-row>
      </div>
      <v-col cols="12" class="mt-16" id="about">
        <div>
          <v-row>
            <v-col cols="12" sm="6">
              <div class="egg">
                <v-img src="../assets/i2.png" max-height="300"></v-img>
              </div>
            </v-col>
            <v-col cols="12" sm="6">
              <h5 style="color: white" class="mt-16">About me</h5>
              <div style="width: 120px">
                <v-slider v-model="slider2" color="yellow" label="track-color">
                </v-slider>
              </div>
              <h4 style="color: white" class="mt-n4">
                I'M a frontend developer
              </h4>
              <p class="text-grey">
                I am a frontend developer who follows and researches the
                developments in technology with curiosity, and who is also
                passionate about software, open minded and open to criticism.
                After graduating from hydraulic engineering at master level, I
                worked in this profession for 2 years.
                <br />
                I could have continued in this area which brought me rigor. But
                the lack of creativity and evolution led me to consider another
                sector. For 6 months I have been digging into the subject and it
                fascinates me. Coding seems particularly fun to me, satisfies my
                permanent desire to learn and brings me a great feeling of
                achievement when the code works.
              </p>
              <v-btn tile dark color="yellow" class="mt-4">
                Download Resume
              </v-btn>
            </v-col>
          </v-row>
        </div>
      </v-col>
      <div class="text-center mt-4">
        <h2 style="color: greenyellow">My projects</h2>
        <v-row justify="center" class="space px-16">
          <v-col cols="12" xs="12" sm="6" md="4"> 

          </v-col>
        </v-row>
      
      </div>
      <Projects/>
    </v-container>
  </v-app>
</template>

<script>

import Projects from '../views/Projects.vue'

export default {
  name: "HomeView",
  setup() {
    return {
      slider2: 50,
    };
  },
  components: {
    Projects,
  },
};
</script>
<style scoped>
.v-container {
  padding: 16px 0 16px 0;
}
.head {
  position: relative;
  text-align: center;
  padding: 12px;
  margin-bottom: 6px;
  height: 400px;
  width: 100%;
  color: white;
}
.head:before {
  content: " ";
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 50%;
  background: black;
  transform: skew(0deg, 6deg);
}
.head:after {
  content: " ";
  position: absolute;
  top: 0;
  right: 0;
  height: 100%;
  width: 50%;
  background: black;
  transform: skew(0deg, -6deg);
}
.egg {
  display: block;
  margin-left: 100px;
  margin-top: 50px;
  width: 356px;
  height: 300px;
  background-color: #fbdf7e;
  border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
}
</style>
