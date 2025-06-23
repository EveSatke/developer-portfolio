<script setup lang="ts">
import { ref } from 'vue'

const profileRef = ref<HTMLElement | null>(null)
const activeSection = ref('about')

const navigationItems = [
  { name: 'About', href: '#about', id: 'about' },
  { name: 'Experience', href: '#experience', id: 'experience' },
  { name: 'Education', href: '#education', id: 'education' },
  { name: 'Projects', href: '#projects', id: 'projects' },
]

const socialLinks = [
  {
    name: 'GitHub',
    href: 'https://github.com/EveSatke',
    icon: `<svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
            <path fill-rule="evenodd" d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z" clip-rule="evenodd" />
          </svg>`,
  },
  {
    name: 'LinkedIn',
    href: 'https://www.linkedin.com/in/evelina-satkauske/',
    icon: `<svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
            <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
          </svg>`,
  },
]

// Add smooth scroll handler
const handleNavClick = (id: string, event: Event) => {
  event.preventDefault()
  activeSection.value = id

  const element = document.getElementById(id)
  if (element) {
    const offset = 80
    const elementPosition = element.getBoundingClientRect().top
    const offsetPosition = elementPosition + window.pageYOffset - offset

    window.scrollTo({
      top: offsetPosition,
      behavior: 'smooth',
    })
  }
}
</script>

<template>
  <div class="h-full flex flex-col justify-between bg-white dark:bg-gray-900">
    <!-- Main Content Container -->
    <div>
      <!-- Name and Title -->
      <div class="space-y-2 mb-8">
        <h1 class="text-2xl lg:text-5xl font-bold">Evelina Satkauskė</h1>
        <p class="text-xl text-gray-600 dark:text-gray-400">Front End Developer | UX Designer</p>
      </div>

      <!-- Profile Container -->
      <div ref="profileRef" class="relative group mb-8">
        <!-- Profile Image Container -->
        <div class="relative w-[100px] h-[100px] rounded-full overflow-hidden">
          <!-- Profile Image -->
          <img src="/profile.png" alt="Evelina Satkauskė" class="w-full h-full object-cover" />
          <!-- Subtle gradient overlay -->
          <div
            class="absolute inset-0 bg-gradient-to-br from-purple-500/5 to-pink-500/5 mix-blend-overlay"
          ></div>
        </div>
      </div>

      <!-- Navigation -->
      <nav class="space-y-6 mb-8">
        <a
          v-for="item in navigationItems"
          :key="item.href"
          :href="item.href"
          class="text-gray-500 dark:text-gray-400 hover:text-gray-900 dark:hover:text-white transition-colors relative group flex items-center"
          :class="{ 'text-gray-900 dark:text-white font-semibold': activeSection === item.id }"
          @click="(e) => handleNavClick(item.id, e)"
        >
          <span
            class="nav-indicator mr-4 h-[2px] transition-all motion-reduce:transition-none"
            :class="[
              activeSection === item.id
                ? 'w-16 bg-gray-900 dark:bg-white'
                : 'w-8 bg-gray-300 dark:bg-gray-600 group-hover:w-16 group-hover:bg-gray-900 dark:group-hover:bg-white',
              'group-focus-visible:w-16 group-focus-visible:bg-gray-900 dark:group-focus-visible:bg-white',
            ]"
          ></span>
          <span class="text-xs uppercase tracking-widest relative z-10">{{ item.name }}</span>
        </a>
      </nav>
    </div>

    <!-- Social Links -->
    <div>
      <div class="flex space-x-6">
        <a
          v-for="link in socialLinks"
          :key="link.name"
          :href="link.href"
          target="_blank"
          rel="noopener noreferrer"
          class="text-gray-600 dark:text-gray-400 hover:text-gray-900 dark:hover:text-white transition-all duration-300"
          v-html="link.icon"
        ></a>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Smooth scroll behavior */
html {
  scroll-behavior: smooth;
}

/* Section transitions */
section {
  transition: opacity 0.3s ease-in-out;
}

/* Optional: Add a subtle hover effect to section headings */
h2 {
  position: relative;
  display: inline-block;
}
</style>
