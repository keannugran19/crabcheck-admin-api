<script setup>
import { RouterView } from 'vue-router'
import SideNav from './components/SideNav.vue'

// import NavBar from './components/NavBar.vue'
</script>

<template>
  <div class="flex">
    <SideNav />
    <!-- Main Content -->
    <RouterView />
  </div>
</template>
