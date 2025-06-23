<script setup lang="ts">
import ProjectCard from '../ui/ProjectCard.vue'

type Skill = {
  name: string
  icon?: string
  category?: 'frontend' | 'backend' | 'tools' | 'design' | 'other'
}

type Project = {
  title: string
  description: string
  imageUrl: string
  projectUrl?: string
  githubUrl: string
  skills: Skill[]
}

const projects: Project[] = [
  {
    title: 'Habits App',
    description: 'Track your daily habits, monitor progress, and build consistent routines.',
    imageUrl: 'public/projects/habits_app.png',
    projectUrl: 'https://evesatke.github.io/habits-app/',
    githubUrl: 'https://github.com/evesatke/habits-app',
    skills: [
      { name: 'Vue.js', category: 'frontend' },
      { name: 'TypeScript', category: 'frontend' },
      { name: 'Tailwind CSS', category: 'frontend' },
      { name: 'Playwright', category: 'tools' },
    ],
  },
  {
    title: 'Typo',
    description:
      'A modern, web-based typing speed test application that helps users measure and improve their typing skills.',
    imageUrl: 'public/projects/typo.png',
    projectUrl: 'https://evesatke.github.io/typo/',
    githubUrl: 'https://github.com/EveSatke/typo',
    skills: [
      { name: 'Vanilla JavaScript', category: 'frontend' },
      { name: 'HTML5', category: 'frontend' },
      { name: 'CSS3', category: 'frontend' },
      { name: 'PoetryDB API', category: 'backend' },
    ],
  },
  {
    title: 'Telia e-shop',
    description:
      'This project is part of the Women Go Tech program, specifically developed as a portfolio project for Telia company.',
    imageUrl: 'public/projects/e-shop.png',
    projectUrl: 'https://evesatke.github.io/telia_e-shop/',
    githubUrl: 'https://github.com/EveSatke/telia_e-shop',
    skills: [
      { name: 'React', category: 'frontend' },
      { name: 'Next.js', category: 'frontend' },
      { name: 'Tailwind CSS', category: 'frontend' },
      { name: 'Jest', category: 'tools' },
    ],
  },
  {
    title: 'Tic-tac-toe game',
    description:
      'Vanilla JavaScript Tic-tac-toe with modular architecture, responsive design, and game state management.',
    imageUrl: 'public/projects/tic-tac-toe.png',
    projectUrl: 'https://evesatke.github.io/tic-tac-toe/',
    githubUrl: 'https://github.com/EveSatke/tic-tac-toe',
    skills: [
      { name: 'Vanilla JavaScript', category: 'frontend' },
      { name: 'HTML5', category: 'frontend' },
      { name: 'CSS3', category: 'frontend' },
    ],
  },
]
</script>

<template>
  <section class="py-10">
    <div class="max-w-3xl mx-auto px-4">
      <div class="grid gap-8 md:grid-cols-2">
        <ProjectCard v-for="(project, i) in projects" :key="i" v-bind="project" />
      </div>
    </div>
  </section>
</template>
