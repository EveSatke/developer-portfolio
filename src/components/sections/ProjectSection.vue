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
    description: 'A web application for tracking daily habits and building positive routines.',
    imageUrl: './projects/habits_app.png',
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
    title: 'Typo Game',
    description: 'A typing speed test game with word generation and accuracy tracking.',
    imageUrl: './projects/typo.png',
    projectUrl: 'https://evesatke.github.io/typo-game/',
    githubUrl: 'https://github.com/evesatke/typo-game',
    skills: [
      { name: 'Vanilla JavaScript', category: 'frontend' },
      { name: 'HTML5', category: 'frontend' },
      { name: 'CSS3', category: 'frontend' },
      { name: 'PoetryDB API', category: 'backend' },
    ],
  },
  {
    title: 'E-Shop',
    description: 'An e-commerce website with product catalog and shopping cart functionality.',
    imageUrl: './projects/e-shop.png',
    projectUrl: 'https://evesatke.github.io/e-shop/',
    githubUrl: 'https://github.com/evesatke/e-shop',
    skills: [
      { name: 'React', category: 'frontend' },
      { name: 'Next.js', category: 'frontend' },
      { name: 'Tailwind CSS', category: 'frontend' },
      { name: 'Jest', category: 'tools' },
    ],
  },
  {
    title: 'Tic Tac Toe',
    description: 'A classic tic-tac-toe game with player turn tracking and win detection.',
    imageUrl: './projects/tic-tac-toe.png',
    projectUrl: 'https://evesatke.github.io/tic-tac-toe/',
    githubUrl: 'https://github.com/evesatke/tic-tac-toe',
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
      <div class="text-right mt-8">
        <a
          href="https://github.com/EveSatke"
          target="_blank"
          rel="noopener noreferrer"
          class="inline-flex items-center gap-2 text-slate-600 hover:text-indigo-600 transition-all duration-300 font-medium group"
        >
          <span class="transition-colors duration-300">More projects on GitHub</span>
          <svg
            class="w-4 h-4 transition-all duration-300 group-hover:translate-x-1 group-hover:text-indigo-600"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M17 8l4 4m0 0l-4 4m4-4H3"
            />
          </svg>
        </a>
      </div>
    </div>
  </section>
</template>
