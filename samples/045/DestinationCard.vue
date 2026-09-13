<script setup>
defineProps({
    destination: Object
});
</script>

<template>
    <div class="col-md-4 d-flex">
        <div class="card shadow w-100">
            <img 
                :src="destination.image" 
                :alt="destination.name" 
                class="card-img-top"
            >
            <div class="card-body d-flex flex-column">
                <h4>
                    {{ destination.name }}
                </h4>
                <p>
                    {{ destination.country }}
                </p>
                <h5 class="text-primary">
                    ${{ destination.price }}
                </h5>
                <button class="btn btn-outline-primary mt-auto">
                    View Package
                </button>
            </div>
        </div>
    </div>
</template>