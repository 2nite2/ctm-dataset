<script setup lang="ts">
import { computed, onBeforeUnmount, onMounted, ref } from 'vue';
import AppHeader from './components/AppHeader.vue';
import HeroSection from './components/HeroSection.vue';

import ProjectShowcase from './components/ProjectShowcase.vue';
import JourneySection from './components/JourneySection.vue';
import ContactSection from './components/ContactSection.vue';
import SiteFooter from './components/SiteFooter.vue';
import {
  brand,
  contacts,
  experiences,
  heroStats,
  navLinks,
  projects,
  rotatingRoles,
  skillTape,
} from './data/portfolio';

const activeSection = ref('home');
const scrollProgress = ref(0);
const scrolled = ref(false);
const roleIndex = ref(0);
const currentRole = computed<string>(() => rotatingRoles[roleIndex.value] ?? 'Vue Product Engineer');
const forwardList = computed(() => [...skillTape, ...skillTape]);
const reverseList = computed(() => [...skillTape].reverse().concat([...skillTape].reverse()));

let roleTimer: number | null = null;
let revealObserver: IntersectionObserver | null = null;

const updateScrollState = () => {
  scrolled.value = window.scrollY > 18;

  const maxScroll = document.documentElement.scrollHeight - window.innerHeight;
  scrollProgress.value = maxScroll > 0 ? window.scrollY / maxScroll : 0;

  const marker = window.scrollY + window.innerHeight * 0.34;

  for (const link of navLinks) {
    const section = document.getElementById(link.id);
    if (!section) {
      continue;
    }

    const top = section.offsetTop;
    const bottom = top + section.offsetHeight;

    if (marker >= top && marker < bottom) {
      activeSection.value = link.id;
    }
  }
};

const updatePointer = (event: MouseEvent) => {
  document.documentElement.style.setProperty('--cursor-x', `${event.clientX}px`);
  document.documentElement.style.setProperty('--cursor-y', `${event.clientY}px`);
};

const setupRevealObserver = () => {
  const nodes = document.querySelectorAll<HTMLElement>('.reveal');

  revealObserver = new IntersectionObserver(
    (entries) => {
      for (const entry of entries) {
        if (entry.isIntersecting) {
          entry.target.classList.add('is-visible');
        }
      }
    },
    { threshold: 0.2 }
  );

  nodes.forEach((node, index) => {
    node.style.setProperty('--reveal-delay', `${(index % 6) * 75}ms`);
    revealObserver?.observe(node);
  });
};

onMounted(() => {
  roleTimer = window.setInterval(() => {
    roleIndex.value = (roleIndex.value + 1) % rotatingRoles.length;
  }, 2300);

  updateScrollState();

  window.addEventListener('scroll', updateScrollState, { passive: true });
  window.addEventListener('resize', updateScrollState);
  window.addEventListener('mousemove', updatePointer, { passive: true });

  setupRevealObserver();
});

onBeforeUnmount(() => {
  if (roleTimer) {
    window.clearInterval(roleTimer);
  }

  window.removeEventListener('scroll', updateScrollState);
  window.removeEventListener('resize', updateScrollState);
  window.removeEventListener('mousemove', updatePointer);

  revealObserver?.disconnect();
});
</script>

<template>
  <div class="site-shell">
    <div class="ambient-layer" aria-hidden="true">
      <span class="orb orb-a" />
      <span class="orb orb-b" />
      <span class="orb orb-c" />
      <span class="grain" />
    </div>

    <AppHeader :links="navLinks" :active-section="activeSection" :scrolled="scrolled" :progress="scrollProgress" />

    <main>
      <section id="home" class="section reveal">
        <HeroSection :brand="brand" :stats="heroStats" :role="currentRole" />
      </section>

      <section id="toolkit" class="section reveal">
        <div class="section-inner grid gap-5">
            <div>
              <p class="m-0 font-['IBM_Plex_Mono'] text-[0.75rem] uppercase tracking-[0.1em] text-[var(--orange)]">Toolkit</p>
              <h2 class="my-2 font-['Syne'] text-[clamp(1.4rem,4vw,2.3rem)]">Stack that ships polished products</h2>
              <p class="m-0 max-w-[70ch] text-[var(--muted)]">
                From architecture to motion details, the workflow keeps design intent and engineering quality aligned.
              </p>
            </div>

            <div
              class="grid gap-2 overflow-hidden [mask-image:linear-gradient(to_right,transparent,_#000_8%,_#000_92%,_transparent)] [-webkit-mask-image:linear-gradient(to_right,transparent,_#000_8%,_#000_92%,_transparent)]"
              aria-label="Technology stack"
            >
              <ul class="m-0 flex w-max list-none gap-2.5 p-0 motion-safe:animate-[slide-left_22s_linear_infinite]">
                <li v-for="(skill, index) in forwardList" :key="`${skill}-${index}`">{{ skill }}</li>
              </ul>
              <ul class="m-0 flex w-max list-none gap-2.5 p-0 motion-safe:animate-[slide-right_30s_linear_infinite]" aria-hidden="true">
                <li v-for="(skill, index) in reverseList" :key="`${skill}-${index}`">{{ skill }}</li>
              </ul>
            </div>
          </div>
      </section>

      <section id="projects" class="section reveal">
        <ProjectShowcase :projects="projects" />
      </section>

      <section id="journey" class="section reveal">
        <JourneySection :items="experiences" />
      </section>

      <section id="contact" class="section reveal">
        <ContactSection :links="contacts" />
      </section>
    </main>

    <SiteFooter :year="new Date().getFullYear()" />
  </div>
</template>


<style scoped>
li {
  border-radius: 999px;
  border: 1px solid rgba(20, 40, 66, 0.14);
  padding: 0.42rem 0.8rem;
  font-size: 0.82rem;
  background: rgba(255, 255, 255, 0.72);
}
</style>
