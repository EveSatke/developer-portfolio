<script setup lang="ts">
import { RouterView } from 'vue-router'
import SidebarNav from './components/SidebarNav.vue'
</script>

<template>
  <div class="min-h-screen w-full bg-white text-slate-900">
    <div
      class="flex flex-col lg:flex-row mx-auto min-h-screen max-w-screen-xl px-6 py-12 font-sans md:px-12 md:py-16 lg:py-0"
    >
      <div
        class="lg:sticky lg:top-0 lg:flex lg:max-h-screen lg:w-[48%] lg:flex-col lg:justify-between lg:py-24"
      >
        <SidebarNav />
      </div>

      <main class="pt-24 lg:w-[52%] lg:py-24">
        <div class="w-full">
          <RouterView />
        </div>
      </main>
    </div>
  </div>
</template>
