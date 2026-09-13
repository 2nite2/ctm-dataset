<script setup>
import Navbar from "./components/Navbar.vue";
import Hero from "./components/Hero.vue";
import destinations from "./data/destinations.js";
import DestinationCard from "./components/DestinationCard.vue";

import Benefits from "./components/Benefits.vue";
import Footer from "./components/Footer.vue";
</script>

<template>
    <Navbar />
    <main>
        <Hero />
        <section class="py-5" id="destinations">
                <div class="container">
                    <h2 class="text-center fw-bold mb-5">
                        Popular Destinations
                    </h2>
                    <div class="row g-4">
                        <DestinationCard
                            v-for=" destination in destinations"
                            :key="destination.id"
                            :destination="destination"
                        />
                    </div>
                </div>
            </section>
        <Benefits />
    </main>
    <Footer />
</template>
