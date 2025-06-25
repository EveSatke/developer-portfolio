<script setup lang="ts">
interface Props {
  name: string
  icon?: string
  category?: 'frontend' | 'backend' | 'tools' | 'design' | 'other'
}

const props = withDefaults(defineProps<Props>(), {
  category: 'other',
})

const getCategoryColor = (category: 'frontend' | 'backend' | 'tools' | 'design' | 'other') => {
  const colors = {
    frontend: 'bg-blue-100 text-blue-800 dark:bg-blue-900/50 dark:text-blue-300',
    backend: 'bg-purple-100 text-purple-800 dark:bg-purple-900/50 dark:text-purple-300',
    tools: 'bg-green-100 text-green-800 dark:bg-green-900/50 dark:text-green-300',
    design: 'bg-pink-100 text-pink-800 dark:bg-pink-900/50 dark:text-pink-300',
    other: 'bg-gray-100 text-gray-800 dark:bg-gray-800/50 dark:text-gray-300',
  }
  return colors[category] || colors.other
}
</script>

<template>
  <div
    class="inline-flex items-center px-3 py-1.5 rounded-full text-sm font-medium transition-transform duration-200 hover:scale-105 cursor-default"
    :class="getCategoryColor(category)"
  >
    <span v-if="icon" class="mr-2">{{ icon }}</span>
    <span>{{ name }}</span>
  </div>
</template>
