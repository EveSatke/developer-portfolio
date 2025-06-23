<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import Sidebar from '@/components/Sidebar.vue'
</script>

<template>
  <div
    class="flex flex-col lg:flex-row mx-auto min-h-screen max-w-screen-xl px-6 py-12 font-sans md:px-12 md:py-16 lg:py-0"
  >
    <!-- Left Side - Sticky Sidebar -->
    <div
      class="lg:sticky lg:top-0 lg:flex lg:max-h-screen lg:w-[48%] lg:flex-col lg:justify-between lg:py-24"
    >
      <Sidebar />
    </div>

    <!-- Right Side - Content -->
    <main class="pt-24 lg:w-[52%] lg:py-24">
      <div class="w-full">
        <RouterView />
      </div>
    </main>
  </div>
</template>
