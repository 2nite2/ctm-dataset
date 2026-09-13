<script setup>
import Navbar from "./components/Navbar.vue";
import Hero from "./components/Hero.vue";
import Destinations from "./components/Destinations.vue";

import Footer from "./components/Footer.vue";
</script>

<template>
    <Navbar />
    <main>
        <Hero />
        <Destinations />
        <section class="py-5 bg-light" id="benefits">
            <div class="container">
              <h2 class="text-center fw-bold mb-5">
                Why Choose TravelHub?
              </h2>

              <div class="row g-4">
                <div class="col-md-4 d-flex">
                  <div class="card shadow w-100 text-center">
                    <div class="card-body d-flex flex-column">
                      <i class="bi bi-globe2 display-4 text-primary mb-3"></i>

                      <h5 class="card-title">
                        Worldwide Destinations
                      </h5>

                      <p class="card-text">
                        Explore amazing destinations across the globe with carefully
                        selected travel experiences.
                      </p>

                      <button class="btn btn-outline-primary mt-auto">
                        Learn More
                      </button>
                    </div>
                  </div>
                </div>

                <div class="col-md-4 d-flex">
                  <div class="card shadow w-100 text-center">
                    <div class="card-body d-flex flex-column">
                      <i class="bi bi-cash-coin display-4 text-success mb-3"></i>

                      <h5 class="card-title">
                        Affordable Packages
                      </h5>

                      <p class="card-text">
                        Enjoy competitive prices and flexible travel packages for every
                        budget.
                      </p>

                      <button class="btn btn-outline-success mt-auto">
                        View Offers
                      </button>
                    </div>
                  </div>
                </div>

                <div class="col-md-4 d-flex">
                  <div class="card shadow w-100 text-center">
                    <div class="card-body d-flex flex-column">
                      <i class="bi bi-headset display-4 text-danger mb-3"></i>

                      <h5 class="card-title">
                        24/7 Support
                      </h5>

                      <p class="card-text">
                        Our support team is available anytime to help make your journey
                        smooth and stress-free.
                      </p>

                      <button class="btn btn-outline-danger mt-auto">
                        Contact Us
                      </button>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </section>
    </main>
    <Footer />
</template>
