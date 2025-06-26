<script setup lang="ts">
interface Props {
  name: string
  icon?: string
  category?: 'frontend' | 'backend' | 'tools' | 'design' | 'other'
  variant?: 'default' | 'compact' | 'outline'
}

const props = withDefaults(defineProps<Props>(), {
  category: 'other',
  variant: 'default',
})

const getCategoryColor = (category: 'frontend' | 'backend' | 'tools' | 'design' | 'other') => {
  const colors = {
    frontend: {
      bg: 'bg-blue-50',
      text: 'text-blue-700',
      border: 'border-blue-200',
      hover: 'hover:bg-blue-100',
    },
    backend: {
      bg: 'bg-purple-50',
      text: 'text-purple-700',
      border: 'border-purple-200',
      hover: 'hover:bg-purple-100',
    },
    tools: {
      bg: 'bg-emerald-50',
      text: 'text-emerald-700',
      border: 'border-emerald-200',
      hover: 'hover:bg-emerald-100',
    },
    design: {
      bg: 'bg-rose-50',
      text: 'text-rose-700',
      border: 'border-rose-200',
      hover: 'hover:bg-rose-100',
    },
    other: {
      bg: 'bg-slate-50',
      text: 'text-slate-700',
      border: 'border-slate-200',
      hover: 'hover:bg-slate-100',
    },
  }
  return colors[category] || colors.other
}

const getVariantClasses = (variant: 'default' | 'compact' | 'outline') => {
  const baseClasses =
    'inline-flex items-center font-medium transition-all duration-200 cursor-default'

  const variants = {
    default: 'px-3 py-1.5 rounded-lg text-sm border',
    compact: 'px-2 py-1 rounded-md text-xs border',
    outline: 'px-3 py-1.5 rounded-lg text-sm border-2 bg-transparent',
  }

  return `${baseClasses} ${variants[variant]}`
}
</script>

<template>
  <div
    :class="[
      getVariantClasses(variant),
      getCategoryColor(category).bg,
      getCategoryColor(category).text,
      getCategoryColor(category).border,
      getCategoryColor(category).hover,
      'hover:scale-105 hover:shadow-sm',
    ]"
  >
    <span v-if="icon" class="mr-1.5 text-xs">{{ icon }}</span>
    <span class="font-medium">{{ name }}</span>
  </div>
</template>
