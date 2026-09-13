<template>
    <ThemeToggleComponent />

    <ShareComponent />
    <!-- <HeaderComponent /> -->
    <img alt="App logo" src="/logo.png" height="105" />
    <!-- <ProfilePage /> -->
    <div class="container">
            <h3 class="title">{{ "@hrwebdevelopers" }}</h3>
            <p class="description">{{ "We build blazing-fast, beautiful websites for startups, small businesses and enterprises." }}</p>
            <div class="links-display">
                <div class="social-link-container">
                    <a class="social-link" href="http://www.facebook.com/hrwebdevelopers" target="_blank" rel="noopener noreferrer">
                        <fa-icon icon="fa-brands fa-facebook" />
                    </a>
                    <a class="social-link" href="http://www.github.com/hrwebdevelopers" target="_blank" rel="noopener noreferrer">
                        <fa-icon icon="fa-brands fa-2xl fa-github" />
                    </a>
                    <a class="social-link" href="https://instagram.com/hrwebdevelopers" target="_blank" rel="noopener noreferrer">
                        <fa-icon icon="fa-brands fa-instagram" />
                    </a>
                    <a class="social-link" href="https://web.whatsapp.com/send?phone=526644727332" target="_blank" rel="noopener noreferrer">
                        <fa-icon icon="fa-brands fa-lg fa-whatsapp" />
                    </a>
                </div>
            </div>
            <h3 class="subtitle">Learn More</h3>
            <div class="link-container">
                <LinkComponent image="/logo.png" title="New Idea or Project? 💡" url="https://www.hr-webdev.com" />
                <LinkComponent image="/favicon.ico" title="We built with VueJS.org Framework V3" url="https://vuejs.org/" />
            </div>
            <h3 class="subtitle">Community Projects</h3>
            <div class="link-container">
                <LinkComponent image="/qr-code.png" title="QR Code Generator" url="https://hectorromerodev.github.io/qr-code-generator/" />
                <LinkComponent image="/excel-to-json.png" title="Excel to JSON" url="https://hectorromerodev.github.io/excel-to-json-v2/" />
            </div>
        </div>
    <!-- <FooterComponent /> -->
</template>

<script>

import ShareComponent from './components/ShareComponent.vue';
import ThemeToggleComponent from './components/ThemeToggleComponent.vue';
import LinkComponent from './components/LinkComponent.vue';

export default {
    name: 'App',
    components: { ShareComponent, ThemeToggleComponent, LinkComponent }
};
</script>

<style>
@import '../public/css/colors.css ';

#app {
    font-family: 'Roboto', sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: var(--font-color);
    background-color: var(--bg-color);
    margin-top: 60px;
}

html {
    height: 100vh;
    width: 100vw;
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    background-color: var(--bg-color);
    color: var(--font-color);
}

body {
    background-color: var(--bg-color);
    color: var(--font-color);
}

a {
    color: var(--font-color);
    text-decoration: none;
    transition: all 0.3s ease;
}

fa-icon {
    color: var(--font-color);
}

h3 {
    margin: 40px 0 0;
}
ul {
    list-style-type: none;
    padding: 0;
}
li {
    display: inline-block;
    margin: 0 10px;
}
.container {
    display: flex;
    flex-direction: column;
}

.social-link-container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: row;
    flex-wrap: wrap;
    gap: 1.25rem;
    width: 100%;
}

.social-link {
    font-size: 2em;
}

.social-link:hover {
    transform: scale(1.1);
}

.link-container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}
</style>
