<template>
    <div
        class="leading-normal tracking-normal text-indigo-400 m-6 bg-cover bg-fixed"
        style="background-image: url('../assets/img/header.png')"
    >
        <div class="h-full">
            <Navbar />
            <main class="container pt-24 md:pt-36 mx-auto flex flex-wrap flex-col md:flex-row items-center">
                <slot />
                <div class="w-full pt-16 pb-6 text-sm text-center md:text-left fade-in">
                    <footer>
                            <a class="text-gray-500 no-underline hover:no-underline" href="#">&copy; App 2020</a> - Template by
                            <a class="text-gray-500 no-underline hover:no-underline" href="https://www.tailwindtoolbox.com"
                                >TailwindToolbox.com</a
                            >
                            <br />
                            Converted to Vue by
                            <a class="text-gray-500 no-underline hover:no-underline" href="https://github.com/hoonsubin">Hoon Kim</a>
                        </footer>
                </div>
            </main>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';


import Navbar from '../components/Navbar.vue';

export default defineComponent({
    components: { Navbar },
});
</script>
