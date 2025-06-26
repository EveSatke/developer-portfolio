<script setup lang="ts">
import { computed } from 'vue'
import SkillBadge from './SkillBadge.vue'

interface Skill {
  name: string
  icon?: string
  category?: 'frontend' | 'backend' | 'tools' | 'design' | 'other'
}

interface Props {
  date: string
  title: string
  institution: string
  institutionUrl?: string
  logoUrl?: string
  skills?: Skill[]
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
    class="relative bg-white border border-slate-200 rounded-xl p-4 transition-all duration-200 hover:bg-violet-50 hover:border-violet-400 hover:scale-[1.01] hover:shadow-lg"
  >
    <div class="flex items-center gap-3">
      <!-- Avatar/Logo on the left -->
      <div
        class="w-8 h-8 flex items-center justify-center border border-slate-100 flex-shrink-0 overflow-hidden"
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
          <span class="text-xs font-bold text-slate-700 select-none">
            {{ getInitials(props.institution) }}
          </span>
        </template>
      </div>

      <!-- Card content on the right -->
      <div class="flex-1 min-w-0">
        <div class="flex flex-col sm:flex-row sm:justify-between sm:items-start gap-2 mb-2">
          <span class="text-xs text-slate-500 font-mono bg-slate-100 px-2 py-1 rounded-md w-fit">{{
            props.date
          }}</span>
          <template v-if="hasInstitutionUrl">
            <a
              :href="props.institutionUrl"
              target="_blank"
              rel="noopener noreferrer"
              class="text-violet-600 hover:text-violet-800 font-semibold text-sm flex items-center group"
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
        <h3 class="font-semibold leading-snug text-slate-900 text-base mb-1">
          {{ props.title }}
        </h3>
        <div class="text-sm text-slate-700 font-semibold mb-2">
          {{ props.institution }}
        </div>

        <!-- Skills Section -->
        <div v-if="props.skills && props.skills.length" class="mt-2">
          <div class="text-xs font-medium text-slate-500 mb-2 uppercase tracking-wide">
            Skills & Focus Areas
          </div>
          <div class="flex flex-wrap gap-2">
            <SkillBadge
              v-for="skill in props.skills"
              :key="skill.name"
              v-bind="skill"
              variant="compact"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
