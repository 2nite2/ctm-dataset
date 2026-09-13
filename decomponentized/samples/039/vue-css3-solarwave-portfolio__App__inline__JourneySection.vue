<script setup lang="ts">
import { computed, onBeforeUnmount, onMounted, ref } from 'vue';
import AppHeader from './components/AppHeader.vue';
import HeroSection from './components/HeroSection.vue';
import SkillsTape from './components/SkillsTape.vue';
import ProjectShowcase from './components/ProjectShowcase.vue';

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
        <SkillsTape :skills="skillTape" />
      </section>

      <section id="projects" class="section reveal">
        <ProjectShowcase :projects="projects" />
      </section>

      <section id="journey" class="section reveal">
        <div class="section-inner">
            <p class="m-0 font-['IBM_Plex_Mono'] text-[0.75rem] uppercase tracking-[0.1em] text-[var(--blue)]">Experience</p>
            <h2 class="mb-6 mt-2 font-['Syne'] text-[clamp(1.5rem,4vw,2.5rem)]">Journey through product and interface teams</h2>

            <div class="relative grid gap-3">
              <div
                class="pointer-events-none absolute bottom-2 top-2 left-[0.55rem] w-0.5 bg-[linear-gradient(to_bottom,var(--teal),var(--orange))] min-[640px]:left-[0.85rem]"
              />

              <article
                v-for="item in experiences"
                :key="`${item.company}-${item.period}`"
                class="relative ml-[1.8rem] rounded-2xl border border-[rgba(20,40,66,0.1)] bg-white/70 p-4 min-[640px]:ml-[2.35rem]"
              >
                <span
                  class="absolute top-[1.1rem] -left-[1.35rem] h-3.5 w-3.5 rounded-full bg-[linear-gradient(130deg,var(--teal),var(--orange))] min-[640px]:-left-[1.73rem]"
                />

                <header class="flex justify-between gap-4">
                  <strong class="font-['Syne'] text-base">{{ item.role }}</strong>
                  <span class="font-['IBM_Plex_Mono'] text-[0.74rem] text-[var(--muted)]">{{ item.period }}</span>
                </header>
                <p class="mb-3 mt-1 text-[0.86rem] text-[var(--blue)]">{{ item.company }}</p>

                <ul class="m-0 grid gap-1.5 pl-4 text-[0.9rem] leading-[1.55] text-[var(--muted)]">
                  <li v-for="highlight in item.highlights" :key="highlight">{{ highlight }}</li>
                </ul>
              </article>
            </div>
          </div>
      </section>

      <section id="contact" class="section reveal">
        <ContactSection :links="contacts" />
      </section>
    </main>

    <SiteFooter :year="new Date().getFullYear()" />
  </div>
</template>
