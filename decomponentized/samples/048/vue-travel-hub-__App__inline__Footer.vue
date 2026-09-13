<script setup>
import Navbar from "./components/Navbar.vue";
import Hero from "./components/Hero.vue";
import Destinations from "./components/Destinations.vue";
import Benefits from "./components/Benefits.vue";

</script>

<template>
    <Navbar />
    <main>
        <Hero />
        <Destinations />
        <Benefits />
    </main>
    <footer class="bg-dark text-white pt-5 pb-3">
            <div class="container">
                <div class="row">
                    <div class="col-lg-4 mb-4">
                        <h4>
                            <i class="bi bi-airplane-fill me-2"></i>
                            TravelHub
                        </h4>
                        <p>
                            Discover unforgettable experiences around the world.
                        </p>
                    </div>
                    <div class="col-lg-4 mb-4">
                        <h5>Quick Links</h5>
                        <ul class="list-unstyled">
                            <li>
                                <a 
                                    class="text-white text-decoration-none"
                                    href="#">
                                    Home
                                </a>
                            </li>
                            <li>
                                <a 
                                    class="text-white text-decoration-none"
                                    href="#destinations">
                                    Destinations
                                </a>
                            </li>
                            <li>
                                <a 
                                    class="text-white text-decoration-none"
                                    href="#packages">
                                    Packages
                                </a>
                            </li>
                            <li>
                                <a 
                                    class="text-white text-decoration-none"
                                    href="#contact">
                                    Contact
                                </a>
                            </li>
                        </ul>
                    </div>
                    <div class="col-lg-4">
                        <h5>Newsletter</h5>
                        <div class="input-group mb-3">
                            <input
                                class="form-control"
                                type="email"
                                placeholder="Email address"
                            >
                            <button class="btn btn-primary">Subscribe</button>
                        </div>
                        <div>
                            <i class="bi bi-facebook me-3"></i>
                            <i class="bi bi-instagram me-3"></i>
                            <i class="bi bi-twitter me-3"></i>
                            <i class="bi bi-youtube me-3"></i>
                        </div>
                    </div>
                </div>
                <hr>
                <p class="text-center mb-0">
                    © 2026 TravelHub. All rights reserved
                </p>
            </div>
        </footer>
</template>
