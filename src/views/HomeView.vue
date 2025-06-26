<script setup lang="ts">
import { onMounted, ref, nextTick, onUnmounted } from 'vue'
import AboutSection from '../components/sections/AboutSection.vue'
import ExperienceSection from '../components/sections/ExperienceSection.vue'
import EducationSection from '../components/sections/EducationSection.vue'
import ProjectSection from '../components/sections/ProjectSection.vue'

const aboutRef = ref(null)
const experienceRef = ref(null)
const educationRef = ref(null)
const projectsRef = ref(null)

const throttle = (func: (...args: unknown[]) => void, limit: number) => {
  let inThrottle: boolean
  return function (...args: unknown[]) {
    if (!inThrottle) {
      func(...args)
      inThrottle = true
      setTimeout(() => (inThrottle = false), limit)
    }
  }
}

const handleScroll = throttle(() => {
  const sections = [
    { id: 'about', ref: aboutRef },
    { id: 'experience', ref: experienceRef },
    { id: 'education', ref: educationRef },
    { id: 'projects', ref: projectsRef },
  ]

  const scrollPosition = window.scrollY + 100

  sections.forEach(({ id, ref }) => {
    if (ref.value) {
      const element = ref.value as HTMLElement
      const rect = element.getBoundingClientRect()
      const offsetTop = rect.top + window.scrollY
      const offsetBottom = offsetTop + rect.height

      if (scrollPosition >= offsetTop && scrollPosition < offsetBottom) {
        window.dispatchEvent(new CustomEvent('sectionChange', { detail: { id } }))
      }
    }
  })
}, 100)

onMounted(() => {
  nextTick(() => {
    const sections = [
      aboutRef.value,
      experienceRef.value,
      educationRef.value,
      projectsRef.value,
    ].filter(Boolean)

    sections.forEach((section, index) => {
      if (section) {
        ;(section as HTMLElement).style.opacity = '0'
        setTimeout(() => {
          ;(section as HTMLElement).style.opacity = '1'
        }, index * 100)
      }
    })

    window.addEventListener('scroll', handleScroll, { passive: true })
    handleScroll()
  })
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <div class="w-full max-w-full lg:max-w-4xl xl:max-w-6xl mx-auto space-y-16 lg:space-y-32">
    <section ref="aboutRef" id="about" class="scroll-mt-20 flex flex-col lg:flex-row justify-start">
      <div class="w-full lg:px-0 text-left">
        <AboutSection name="Evelina Satkauskė" />
      </div>
    </section>

    <section ref="experienceRef" id="experience" class="scroll-mt-20">
      <div class="w-full lg:px-0">
        <div class="space-y-8">
          <ExperienceSection />
        </div>
      </div>
    </section>

    <section ref="educationRef" id="education" class="scroll-mt-20">
      <div class="w-full lg:px-0">
        <div class="space-y-8">
          <EducationSection />
        </div>
      </div>
    </section>

    <section ref="projectsRef" id="projects" class="scroll-mt-20">
      <div class="w-full lg:px-0">
        <ProjectSection />
      </div>
    </section>
  </div>
</template>
