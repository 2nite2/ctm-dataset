<template>
    <div class="theme-switch-wrapper">
            <label class="theme-switch" for="checkbox">
                <input type="checkbox" id="checkbox" @change="switchTheme($event)" />
                <div class="slider round"></div>
            </label>
            <em>{{ theme }}</em>
        </div>

    <ShareComponent />
    <!-- <HeaderComponent /> -->
    <img alt="App logo" src="/logo.png" height="105" />
    <!-- <ProfilePage /> -->
    <SocialMediaLinks title="@hrwebdevelopers" description="We build blazing-fast, beautiful websites for startups, small businesses and enterprises." />
    <!-- <FooterComponent /> -->
</template>

<script>
import SocialMediaLinks from './components/SocialMediaLinks.vue';
import ShareComponent from './components/ShareComponent.vue';


export default {
    name: 'App',
    components: { SocialMediaLinks, ShareComponent },
    data() {
        return {
            theme: localStorage.getItem('theme') === 'dark' ? 'dark' : 'light'
        };
    },
    methods: {
        switchTheme(e) {
            const toggleInput = document.getElementById('checkbox');
            const isDark = e?.target.checked || toggleInput?.checked;
            if (isDark) {
                this.theme = 'dark';
                document.documentElement.setAttribute('data-theme', 'dark');
                localStorage.setItem('theme', 'dark');
            } else {
                this.theme = 'light';
                document.documentElement.setAttribute('data-theme', this.theme);
            }
        }
    },
    created() {
        this.switchTheme();
    }
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

/* BACKGROUND */

.theme-switch-wrapper {
    position: fixed;
    align-items: center;
    top: 1.5rem;
    height: 2rem;
    right: calc(100vw - 10% - 2rem);
}

.theme-switch-wrapper em {
    /* margin-left: 10px; */
    position: absolute;
    top: -1.125rem;
    left: 1rem;
    /* font-size: 1rem; */
}

.theme-switch {
    display: inline-block;
    /* height: 34px; */
    height: 2rem;
    position: relative;
    width: 60px;
}

.theme-switch input {
    display: none;
}

.slider {
    background-color: var(--bg-color);
    bottom: 0;
    cursor: pointer;
    left: 0;
    position: absolute;
    right: 0;
    top: 0;
    transition: 0.4s;
}

.slider:before {
    background-color: var(--font-color);
    bottom: 4px;
    content: '';
    height: 26px;
    left: 4px;
    position: absolute;
    transition: 0.4s;
    width: 26px;
}

input:checked + .slider {
    background-color: var(--bg-color);
}

input:checked + .slider:before {
    transform: translateX(26px);
}

.slider.round {
    border-radius: 50px;
    background: var(--bg-color);
    box-shadow: 3px 3px 7px var(--box-shadow-top-color), -3px -3px 7px var(--box-shadow-bottom-color);
}

.slider.round:hover {
    background: var(--bg-color);
}

.slider.round:before {
    border-radius: 50%;
}

/* BACKGROUND */
</style>
