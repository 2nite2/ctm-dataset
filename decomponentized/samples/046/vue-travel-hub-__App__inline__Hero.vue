<script setup>
import Navbar from "./components/Navbar.vue";

import Destinations from "./components/Destinations.vue";
import Benefits from "./components/Benefits.vue";
import Footer from "./components/Footer.vue";

function explorePackage() {
    alert("Let's explore the world!");
}
</script>

<template>
    <Navbar />
    <main>
        <section class="hero bg-light py-5">
                <div class="container text-center">
                    <h1 class="display-3 fw-bold">
                        Discover Your Next Adventure
                    </h1>
                    <p class="lead my-4">
                        Explore beautiful destinations around the word
                        with exclusive travel packages
                    </p>
                    <button class="btn btn-primary btn-lg" @click="explorePackage">
                        Explore Package
                    </button>
                </div>
            </section>
        <Destinations />
        <Benefits />
    </main>
    <Footer />
</template>
