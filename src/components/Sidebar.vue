<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const profileRef = ref<HTMLElement | null>(null)
const activeSection = ref('about')
const emailCopied = ref(false)
const cvDownloaded = ref(false)

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

const copyEmail = async () => {
  try {
    await navigator.clipboard.writeText('evelina.satkauske@gmail.com')
    emailCopied.value = true
    setTimeout(() => {
      emailCopied.value = false
    }, 2000)
  } catch (err) {
    console.error('Failed to copy email:', err)
  }
}

const downloadCV = () => {
  const link = document.createElement('a')
  link.href = '/resume.pdf'
  link.download = 'Evelina_Satkauske_CV.pdf'
  document.body.appendChild(link)
  link.click()
  document.body.removeChild(link)

  cvDownloaded.value = true
  setTimeout(() => {
    cvDownloaded.value = false
  }, 2000)
}

// Listen for section changes from scroll
const handleSectionChange = (event: CustomEvent) => {
  activeSection.value = event.detail.id
}

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

onMounted(() => {
  window.addEventListener('sectionChange', handleSectionChange as EventListener)
})

onUnmounted(() => {
  window.removeEventListener('sectionChange', handleSectionChange as EventListener)
})
</script>

<template>
  <div class="h-full flex flex-col justify-between bg-white">
    <!-- Main Content Container -->
    <div class="flex flex-col h-full">
      <!-- 1. Profile Section: Photo + Info Side by Side -->
      <div class="mb-8">
        <!-- Profile Photo and Info Layout -->
        <div class="flex items-start space-x-4">
          <!-- Profile Photo -->
          <div ref="profileRef" class="relative group flex-shrink-0">
            <div class="relative w-[100px] h-[100px] rounded-full overflow-hidden">
              <img src="/profile.png" alt="Evelina Satkauskė" class="w-full h-full object-cover" />
              <div
                class="absolute inset-0 bg-gradient-to-br from-purple-500/5 to-pink-500/5 mix-blend-overlay"
              ></div>
            </div>
          </div>

          <!-- Name, Position, Email - Vertical stack next to photo -->
          <div class="flex flex-col justify-center space-y-1">
            <h1 class="text-2xl lg:text-4xl font-bold text-slate-900">Evelina Satkauskė</h1>

            <p class="text-lg text-gray-600">Front End Developer | UX Designer</p>

            <button
              @click="copyEmail"
              class="group flex items-center space-x-2 text-gray-600 hover:text-gray-900 transition-colors cursor-pointer"
            >
              <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M3 8l7.89 4.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"
                />
              </svg>
              <span class="text-sm font-medium">evelina.satkauske@gmail.com</span>
              <span v-if="emailCopied" class="text-xs text-green-600 ml-2"> Copied! </span>
            </button>
          </div>
        </div>
      </div>

      <nav class="flex-1 flex flex-col justify-start pl-4 py-8">
        <div class="space-y-6">
          <a
            v-for="item in navigationItems"
            :key="item.href"
            :href="item.href"
            class="text-gray-500 hover:text-gray-900 transition-colors relative group flex items-center"
            :class="{
              'text-gray-900 font-semibold': activeSection === item.id,
            }"
            @click="(e) => handleNavClick(item.id, e)"
          >
            <span
              class="nav-indicator mr-4 h-[2px] transition-all motion-reduce:transition-none"
              :class="[
                activeSection === item.id
                  ? 'w-16 bg-gray-900'
                  : 'w-8 bg-gray-300 group-hover:w-16 group-hover:bg-gray-900',
                'group-focus-visible:w-16 group-focus-visible:bg-gray-900',
              ]"
            ></span>
            <span class="text-xs uppercase tracking-widest relative z-10">{{ item.name }}</span>
          </a>
        </div>
      </nav>
    </div>

    <!-- 3. Resume Button and Social Links - Bottom with padding -->
    <div class="pl-4 pb-4">
      <div class="flex items-center space-x-4">
        <!-- Resume Button - Black -->
        <button
          @click="downloadCV"
          class="inline-flex items-center px-4 py-2 bg-black text-white rounded-lg hover:bg-gray-800 hover:cursor-pointer transition-all duration-300 font-medium text-sm"
          title="Download Resume"
        >
          <svg class="w-4 h-4 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M12 10v6m0 0l-3-3m3 3l3-3m2 8H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"
            />
          </svg>
          Resume
          <span v-if="cvDownloaded" class="text-xs text-green-400 ml-2"> ✓ </span>
        </button>

        <!-- Social Links -->
        <div class="flex items-center space-x-2">
          <a
            v-for="link in socialLinks"
            :key="link.name"
            :href="link.href"
            target="_blank"
            rel="noopener noreferrer"
            class="text-gray-500 hover:text-gray-700 transition-all duration-300 p-2 rounded-lg hover:bg-gray-100"
            :title="link.name"
            v-html="link.icon"
          ></a>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
html {
  scroll-behavior: smooth;
}

section {
  transition: opacity 0.3s ease-in-out;
}

h2 {
  position: relative;
  display: inline-block;
}
</style>
