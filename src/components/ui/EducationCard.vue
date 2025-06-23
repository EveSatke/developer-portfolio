<script setup lang="ts">
import { computed } from 'vue'

interface Props {
  date: string
  title: string
  institution: string
  institutionUrl?: string
  logoUrl?: string
}

const props = defineProps<Props>()

function getInitials(name: string) {
  return name
    .split(' ')
    .map((word) => word[0])
    .join('')
    .toUpperCase()
}

const hasLogo = computed(() => !!props.logoUrl && props.logoUrl.trim() !== '')
const hasInstitutionUrl = computed(
  () => !!props.institutionUrl && props.institutionUrl.trim() !== '',
)
</script>

<template>
  <div
    class="relative bg-white dark:bg-slate-800 border border-slate-200 dark:border-slate-700 rounded-xl p-6 transition-all duration-200 flex items-center hover:bg-violet-50 dark:hover:bg-violet-900 hover:border-violet-400 hover:scale-[1.01]"
  >
    <!-- Avatar/Logo on the left -->
    <div
      class="w-8 h-8 mr-4 flex items-center justify-center border border-slate-100 dark:border-slate-600 flex-shrink-0 overflow-hidden"
      :class="!hasLogo ? 'rounded-full' : 'rounded-md'"
      :style="!hasLogo ? { background: 'var(--color-avatar-purple)' } : {}"
    >
      <template v-if="hasLogo">
        <img
          :src="props.logoUrl"
          :alt="props.institution + ' logo'"
          class="w-full h-full object-contain"
        />
      </template>
      <template v-else>
        <span class="text-xs font-bold text-slate-700 dark:text-slate-200 select-none">
          {{ getInitials(props.institution) }}
        </span>
      </template>
    </div>
    <!-- Card content on the right -->
    <div class="flex-1">
      <div class="flex flex-col sm:flex-row sm:justify-between sm:items-center">
        <span class="text-xs text-slate-500 dark:text-slate-400 font-mono">{{ props.date }}</span>
        <template v-if="hasInstitutionUrl">
          <a
            :href="props.institutionUrl"
            target="_blank"
            rel="noopener noreferrer"
            class="text-violet-600 dark:text-violet-400 hover:text-violet-800 dark:hover:text-violet-300 font-semibold text-sm mt-1 sm:mt-0 flex items-center"
          >
            {{ props.institution }}
            <!-- External link icon -->
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="inline-block h-4 w-4 ml-1 align-text-bottom"
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
        </template>
      </div>
      <h3 class="font-semibold leading-snug text-slate-900 dark:text-slate-200 text-lg mt-2">
        {{ props.title }}
      </h3>
      <div class="mt-1 text-sm text-slate-700 dark:text-slate-300 font-semibold">
        {{ props.institution }}
      </div>
    </div>
  </div>
</template>
