<script setup lang="ts">
import { ref, onMounted } from 'vue';
import { useRoute } from 'vue-router';
import { projects, type Project } from '@/data/projects';

const route = useRoute();
const projectId = route.params.projectId as string;

const project = ref<Project | null>(null);

onMounted(() => {
  project.value = projects.find(p => p.id === projectId) ?? null;
});
</script>

<template>
  <v-container v-if="project" class="py-12">
    <h1 class="text-h3 font-weight-bold mb-6">{{ project.title }}</h1>
    <p class="text-body-1 mb-4">{{ project.details }}</p>
    <v-btn v-for="link in project.links" color="primary" :href="link.url" target="_blank" class="me-4">{{ link.title }}</v-btn>
    <v-btn color="primary" to="/">Back to Home</v-btn>
  </v-container>

  <v-container v-else class="py-12">
    <p>Project not found.</p>
    <v-btn color="primary" to="/">Back to Home</v-btn>
  </v-container>
</template>

<style scoped></style>