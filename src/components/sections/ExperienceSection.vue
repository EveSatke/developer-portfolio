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
    title: 'UI/UX Designer',
    company: 'Danske Bank',
    companyUrl: 'https://danskebank.com/',
    description: `Led design initiatives for bank employee applications within the Mobile First Technology team, developing prototypes and wireframes across multiple platforms. Conducted comprehensive UX research including user interviews, focus groups, usability testing, and analytics analysis to inform design decisions. Collaborated closely with developers to communicate design rationale, review implementations, and ensure design quality throughout the development process.`,
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
    description: `Selected as one of four students through competitive job interviews for a comprehensive learning program. Over six months, I immersed myself in both front-end and back-end development, mastering Angular, project architecture, and full-stack development. Working closely with mid and senior developers, I participated in hackathons, built complete applications from ideation to deployment, and learned agile methodologies through sprint-based workflows. I gained deep insights into enterprise architecture and banking system capabilities while collaborating in cross-functional teams. After the student period, I was hired as a UX Software Engineer, balancing 50% coding and 50% design work before transitioning to focus exclusively on design.`,
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
