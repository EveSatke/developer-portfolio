<script setup lang="ts">
import ExpierenceCard from '../ui/ExpierenceCard.vue'

type Skill = {
  name: string
  icon?: string
  category?: 'frontend' | 'backend' | 'tools' | 'design' | 'other'
}

type Experience = {
  date: string
  title: string
  company: string
  companyUrl: string
  description: string
  skills: Skill[]
}

const experiences: Experience[] = [
  {
    date: '2019 — 2023',
    title: 'UI UX Designer',
    company: 'Danske Bank',
    companyUrl: 'https://danskebank.com/',
    description: `-Create and lead design in various projects intended for bank employees in Mobile First Technology team
-Create prototypes and wireframes for multiple platforms 
-Conduct UX Research (interviews, focus groups, usability testing, analytics)`,
    skills: [
      { name: 'Figma / Prototyping', category: 'design' },
      { name: 'UX Research', category: 'design' },
      { name: 'UX Writing', category: 'design' },
      { name: 'Agile Development', category: 'tools' },
    ],
  },
  {
    date: '2019 — 2019',
    title: 'IT Software Engineer, student',
    company: 'Danske Bank',
    companyUrl: 'https://danskebank.com/',
    description: `We were 4 students who passed the selection in the job interviews. Half of the year we were learning and doing various projects. I have tried both, front-end and back-end coding. After student period I got hired as UX Software Engineer. I was 50% coding, 50% designing. Later, I have decided to do only design.`,
    skills: [
      { name: 'JavaScript', category: 'frontend' },
      { name: 'TypeScript', category: 'frontend' },
      { name: 'HTML & SCSS', category: 'frontend' },
      { name: 'Angular', category: 'frontend' },
      { name: 'Node.js', category: 'backend' },
    ],
  },
  {
    date: '2017 — 2018',
    title: 'Web Designer',
    company: 'Starflix',
    companyUrl: 'https://www.starflix.lt/',
    description: `After Code Academy web design courses I was doing an internship at Starflix agency. After 3 months I got hired to a web designer/developer position. My responsibilities included creating designs for small companies using WordPress platform, adjust the CSS code, logo design, making brandbooks and etc.`,
    skills: [
      { name: 'WordPress', category: 'frontend' },
      { name: 'CSS', category: 'frontend' },
      { name: 'Logo Design', category: 'design' },
      { name: 'Brandbook', category: 'design' },
    ],
  },
  // Add more experiences as needed
]
</script>

<template>
  <section class="py-10">
    <div class="max-w-3xl mx-auto px-4">
      <div class="space-y-8">
        <ExpierenceCard v-for="(exp, i) in experiences" :key="i" v-bind="exp" />
      </div>
    </div>
  </section>
</template>
