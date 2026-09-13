<script setup>
import destinations from "../data/destinations.js";
import DestinationCard from "./DestinationCard.vue";
</script>

<template>
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
</template>