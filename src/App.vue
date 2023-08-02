<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import Navigation from './components/Navigation.vue'
</script>

<template>
  <Navigation />
  <section class="content">
    <RouterView />
  </section>
</template>

<style scoped>
</style>
