<script setup lang="ts">
import SkillBadge from './SkillBadge.vue'

interface Skill {
  name: string
  icon?: string
  category?: 'frontend' | 'backend' | 'tools' | 'design' | 'other'
}

interface Props {
  date: string
  title: string
  company: string
  companyUrl: string
  description: string
  skills: Skill[]
}

const props = defineProps<Props>()
</script>

<template>
  <div
    class="relative bg-white dark:bg-slate-800 border border-slate-200 dark:border-slate-700 rounded-xl p-6 transition-all duration-200 hover:bg-teal-50 dark:hover:bg-teal-900 hover:border-teal-400 hover:scale-[1.01]"
  >
    <div class="flex flex-col sm:flex-row sm:justify-between sm:items-center mb-2">
      <span class="text-xs text-slate-500 dark:text-slate-400 font-mono">{{ props.date }}</span>
      <a
        :href="props.companyUrl"
        target="_blank"
        rel="noopener noreferrer"
        class="text-teal-600 dark:text-teal-400 hover:text-teal-800 dark:hover:text-teal-300 font-semibold text-sm mt-1 sm:mt-0 flex items-center"
      >
        {{ props.company }}
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="inline-block h-4 w-4 ml-1 align-text-bottom text-teal-600 dark:text-teal-400 group-hover:text-teal-800 dark:group-hover:text-teal-300 transition-colors"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            d="M18 13v6a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          />
          <polyline
            points="15 3 21 3 21 9"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          />
          <line
            x1="10"
            y1="14"
            x2="21"
            y2="3"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          />
        </svg>
      </a>
    </div>
    <h3 class="font-semibold leading-snug text-slate-900 dark:text-slate-200 text-lg mt-2">
      {{ props.title }}
    </h3>
    <p class="text-sm text-slate-700 dark:text-slate-300 mb-3">{{ props.description }}</p>
    <ul class="flex flex-wrap mt-2" aria-label="Technologies used">
      <li v-for="skill in props.skills" :key="skill.name" class="mr-2 mt-2">
        <SkillBadge v-bind="skill" />
      </li>
    </ul>
  </div>
</template>
