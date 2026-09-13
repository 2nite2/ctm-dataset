<template>
  <v-app-bar app color="black" dark flat class="px-12">
    <v-btn icon>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="100%"
        height="100%"
        fill="currentColor"
        class="bi bi-emoji-wink-fill"
        viewBox="0 0 16 16"
        color="yellow"
      >
        <path
          d="M8 0a8 8 0 1 1 0 16A8 8 0 0
              1 8 0zM7 6.5C7 5.672 6.552 5 6 5s-1 
              .672-1 1.5S5.448 8 6 8s1-.672 1-1.5zM4.285 9.567a.5.5 
              0 0 0-.183.683A4.498 4.498 0 0 0 8 12.5a4.5 4.5 0 0
               0 3.898-2.25.5.5 0 1 0-.866-.5A3.498 3.498 0 
               0 1 8 11.5a3.498 3.498 0 0 1-3.032-1.75.5.5
                0 0 0-.683-.183zm5.152-3.31a.5.5 0 0 0-.874.486
                c.33.595.958 1.007 1.687 1.007.73 0 1.356-.412 
                1.687-1.007a.5.5 0 0 0-.874-.486.934.934 0 
                0 1-.813.493.934.934 0 0 1-.813-.493z"
        />
      </svg>
    </v-btn>

    <v-spacer></v-spacer>
    <v-btn color="yellow" @click="goHome()">Home</v-btn>
    <v-btn @click="goProject()" >Project</v-btn>
    <v-btn @click="goAbout()" >about</v-btn>
    <v-btn @click="goContact()"> contact</v-btn>
  </v-app-bar>
</template>

<script>
export default {
  name: "NavBar",
  methods: {
    goProject() {
      this.$router.push('/project')
    },
    goHome() {
      this.$router.push('/')
    },
    goContact () {
      this.$router.push('/contact')
    },
    goAbout () {
      this.$router.push('/about')
    }
  
  
  },
};
</script>

<style></style>
