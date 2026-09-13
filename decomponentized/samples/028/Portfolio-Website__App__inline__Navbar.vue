<script setup lang="ts">

</script>

<template>
  <v-app>
    <v-app-bar app>
        <v-toolbar-title>Portfolio</v-toolbar-title>
        <v-btn text to="/">Home</v-btn>
        <v-btn text to="/about">About Me</v-btn>
        <v-btn text to="/projects">Projects</v-btn>
        <v-btn text to="/contact">Contact Me</v-btn>
      </v-app-bar>
    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<style scoped></style>
