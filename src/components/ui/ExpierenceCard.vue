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
    class="relative bg-white border border-slate-200 rounded-xl p-4 transition-all duration-200 hover:bg-teal-50 hover:border-teal-400 hover:scale-[1.01] hover:shadow-lg"
  >
    <div class="flex flex-col sm:flex-row sm:justify-between sm:items-start gap-2 mb-2">
      <span class="text-xs text-slate-500 font-mono bg-slate-100 px-2 py-1 rounded-md w-fit">{{
        props.date
      }}</span>
      <a
        :href="props.companyUrl"
        target="_blank"
        rel="noopener noreferrer"
        class="text-teal-600 hover:text-teal-800 font-semibold text-sm flex items-center group"
      >
        {{ props.company }}
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="inline-block h-4 w-4 ml-1 align-text-bottom text-teal-600 group-hover:text-teal-800 transition-colors"
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
    <h3 class="font-semibold leading-snug text-slate-900 text-base mb-1">
      {{ props.title }}
    </h3>
    <p class="text-sm text-slate-700 mb-3 leading-relaxed">
      {{ props.description }}
    </p>

    <!-- Skills Section -->
    <div v-if="props.skills.length" class="mt-2">
      <div class="text-xs font-medium text-slate-500 mb-2 uppercase tracking-wide">
        Technologies & Skills
      </div>
      <div class="flex flex-wrap gap-2">
        <SkillBadge
          v-for="skill in props.skills"
          :key="skill.name"
          v-bind="skill"
          variant="default"
        />
      </div>
    </div>
  </div>
</template>
