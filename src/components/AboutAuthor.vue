<script setup lang="ts">
defineProps<{
  name: string
}>()
</script>

<template>
  <div class="about-author">
    <h1 class="green">{{ name }}</h1>
    <h3>Front End Developer | UX Designer</h3>
    <h4>Vue.js | React | Figma</h4>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.about-author h1,
.about-author h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .about-author h1,
  .about-author h3 {
    text-align: left;
  }
}
</style>
