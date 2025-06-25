<script setup lang="ts">
import EducationCard from '../ui/EducationCard.vue'

type Education = {
  date: string
  title: string
  institution: string
  institutionUrl?: string
  logoUrl?: string
}

const education: Education[] = [
  {
    date: '2024 — present',
    title: 'Web Development',
    institution: 'Turing College',
    institutionUrl: 'https://www.turingcollege.com/',
    logoUrl: '/Turing_College_logo.jpeg',
  },
  {
    date: '2020',
    title: 'UX/UI courses Usability ISO',
    institution: 'Greta Galubauskaite',
  },
  {
    date: '2017',
    title: 'Web Design',
    institution: 'Code Academy',
    institutionUrl: 'https://codeacademy.lt/',
    logoUrl: '/codeacademy-black.svg',
  },
  {
    date: '2010 — 2014',
    title: `Bachelor's in Economics of Finance`,
    institution: 'Mykolo Romerio University',
    institutionUrl: 'https://www.mruni.eu/en/',
    logoUrl: '/mru_logo.png',
  },
  // Add more education entries as needed
]
</script>

<template>
  <section class="py-10">
    <div class="max-w-3xl mx-auto px-4">
      <div class="space-y-8">
        <EducationCard v-for="(edu, i) in education" :key="i" v-bind="edu" />
      </div>
    </div>
  </section>
</template>
