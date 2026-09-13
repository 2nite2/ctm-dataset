<script setup>
import { ref } from 'vue';

const search = ref("");

function searchDestination() {
    alert(`Searching for: ${search.value}`);
}
</script>

<template>
    <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
        <div class="container">
            <a class="navbar-brand fw-bold" href="#">
                <i class="bi bi-airplane-fill me-2"></i>
                TravelHub
            </a>
            <button
                class="navbar-toggler"
                type="button"
                data-bs-toggle="collapse"
                data-bs-target="navbar"
            >
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbar">
                <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                    <li class="nav-item">
                        <a class="nav-link active" href="#">Home</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#destinations">Destinations</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#package">Package</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#contact">Contact</a>
                    </li>
                </ul>
                <form  class="d-flex" @submit.prevent="searchDestination">
                    <input 
                        class="form-control me-2"
                        type="search" 
                        placeholder="Search..." 
                        v-model="search"
                    >
                    <button class="btn btn-light">
                        Search
                    </button>
                </form>
            </div>
        </div>
    </nav>
</template>