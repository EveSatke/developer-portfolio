<script setup lang="ts">
import SkillBadge from './SkillBadge.vue'

interface Skill {
  name: string
  icon?: string
  category?: 'frontend' | 'backend' | 'tools' | 'design' | 'other'
}

interface Props {
  title: string
  description: string
  imageUrl: string
  projectUrl?: string
  githubUrl: string
  skills: Skill[]
}

const props = defineProps<Props>()
</script>

<template>
  <div
    class="relative bg-white dark:bg-slate-800 border border-slate-200 dark:border-slate-700 rounded-xl overflow-hidden transition-all duration-200 hover:bg-indigo-50 dark:hover:bg-indigo-900 hover:border-indigo-400 hover:scale-[1.01]"
  >
    <div
      class="w-full aspect-[4/3] bg-gray-100 dark:bg-slate-700 flex items-center justify-center overflow-hidden rounded-t-xl"
    >
      <img
        :src="props.imageUrl"
        :alt="props.title"
        class="w-full h-full object-cover rounded-t-xl"
        loading="lazy"
      />
    </div>

    <!-- Project Content -->
    <div class="p-6">
      <div class="flex items-center justify-between mb-2">
        <h3 class="font-semibold text-lg text-slate-900 dark:text-slate-200">
          {{ props.title }}
        </h3>
      </div>

      <p class="text-sm text-slate-700 dark:text-slate-300 mb-4">
        {{ props.description }}
      </p>

      <div class="flex items-center gap-2 mb-4">
        <a
          v-if="props.projectUrl"
          :href="props.projectUrl"
          target="_blank"
          rel="noopener noreferrer"
          class="inline-flex items-center gap-1 px-3 py-1.5 text-xs font-medium bg-indigo-600 text-white rounded-md hover:bg-indigo-700 transition-colors"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-3 w-3"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"
            />
          </svg>
          Live Demo
        </a>
        <a
          v-if="props.githubUrl"
          :href="props.githubUrl"
          target="_blank"
          rel="noopener noreferrer"
          class="inline-flex items-center gap-1 px-3 py-1.5 text-xs font-medium bg-slate-700 text-white rounded-md hover:bg-slate-800 transition-colors"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-3 w-3"
            viewBox="0 0 24 24"
            fill="currentColor"
          >
            <path
              d="M12 2C6.477 2 2 6.484 2 12.021c0 4.428 2.865 8.184 6.839 9.504.5.092.682-.217.682-.483 0-.237-.009-.868-.014-1.703-2.782.605-3.369-1.342-3.369-1.342-.454-1.155-1.11-1.463-1.11-1.463-.908-.62.069-.608.069-.608 1.004.07 1.532 1.032 1.532 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.339-2.221-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.025A9.564 9.564 0 0 1 12 6.844c.85.004 1.705.115 2.504.337 1.909-1.295 2.748-1.025 2.748-1.025.546 1.378.202 2.397.1 2.65.64.7 1.028 1.595 1.028 2.688 0 3.847-2.337 4.695-4.566 4.944.359.309.678.919.678 1.852 0 1.336-.012 2.415-.012 2.744 0 .268.18.579.688.481C19.138 20.2 22 16.447 22 12.021 22 6.484 17.523 2 12 2Z"
            />
          </svg>
          Code
        </a>
      </div>

      <div v-if="props.skills.length" class="mb-2">
        <div class="font-semibold text-xs text-slate-500 dark:text-slate-400 mb-1">
          Technologies Used
        </div>
        <div class="flex flex-wrap gap-2">
          <SkillBadge v-for="skill in props.skills" :key="skill.name" v-bind="skill" />
        </div>
      </div>
    </div>
  </div>
</template>
