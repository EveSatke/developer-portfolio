<script setup lang="ts">
import { onMounted, ref, nextTick, onUnmounted } from 'vue'
import gsap from 'gsap'
import AboutSection from '../components/sections/AboutSection.vue'
import ExperienceSection from '../components/sections/ExperienceSection.vue'
import EducationSection from '../components/sections/EducationSection.vue'
import ProjectSection from '../components/sections/ProjectSection.vue'

const aboutRef = ref(null)
const experienceRef = ref(null)
const educationRef = ref(null)
const projectsRef = ref(null)

// Add scroll handler
const handleScroll = () => {
  const sections = [
    { id: 'about', ref: aboutRef },
    { id: 'experience', ref: experienceRef },
    { id: 'education', ref: educationRef },
    { id: 'projects', ref: projectsRef },
  ]

  const scrollPosition = window.scrollY + 100 // Fixed offset for header

  sections.forEach(({ id, ref }) => {
    if (ref.value) {
      const element = ref.value as HTMLElement
      const rect = element.getBoundingClientRect()
      const offsetTop = rect.top + window.scrollY
      const offsetBottom = offsetTop + rect.height

      // Check if the section is in view
      if (scrollPosition >= offsetTop && scrollPosition < offsetBottom) {
        window.dispatchEvent(new CustomEvent('sectionChange', { detail: { id } }))
      }
    }
  })
}

onMounted(() => {
  nextTick(() => {
    const sections = [
      aboutRef.value,
      experienceRef.value,
      educationRef.value,
      projectsRef.value,
    ].filter(Boolean)

    gsap.fromTo(sections, { opacity: 0 }, { opacity: 1, duration: 0.3, stagger: 0.1 })

    // Add scroll listener
    window.addEventListener('scroll', handleScroll)
    // Initial check
    handleScroll()
  })
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <div class="w-full max-w-full lg:max-w-4xl xl:max-w-6xl mx-auto space-y-16 lg:space-y-32">
    <!-- About Section -->
    <section ref="aboutRef" id="about" class="scroll-mt-20 flex flex-col lg:flex-row justify-start">
      <div class="w-full lg:px-0 text-left">
        <AboutSection name="Evelina Satkauskė" />
      </div>
    </section>

    <!-- Experience Section -->
    <section ref="experienceRef" id="experience" class="scroll-mt-20">
      <div class="w-full lg:px-0">
        <div class="space-y-8">
          <ExperienceSection />
        </div>
      </div>
    </section>

    <!-- Education Section -->
    <section ref="educationRef" id="education" class="scroll-mt-20">
      <div class="w-full lg:px-0">
        <EducationSection />
      </div>
    </section>

    <!-- Projects Section -->
    <section ref="projectsRef" id="projects" class="scroll-mt-20">
      <div class="w-full lg:px-0">
        <ProjectSection />
      </div>
    </section>
  </div>
</template>

<style>
/* Global styles should be in base.css or App.vue */
</style>

<style scoped>
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
