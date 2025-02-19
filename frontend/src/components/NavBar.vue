<script setup>
import { ref } from 'vue'
// import AppLogo from './AppLogo.vue'

let currentUser = ref('keannugran@gmail.net')
</script>

<template>
  <nav class="bg-gray-100">
    <div class="max-w-7xl mx-auto px-10 sm:px-6 lg:px-8">
      <div class="flex justify-end h-16">
        <!-- <div class="flex items-center">
          <AppLogo class="h-10 w-auto" />
          <img class="h-8 w-auto" src="./assets/images/crabLogo.png" alt="Logo" />
          <span class="ml-2 text-xl font-semibold text-orange-500"> CrabCheck </span>
        </div> -->

        <div class="flex items-center">
          <span class="text-gray-600"> {{ currentUser }} </span>
        </div>
      </div>
    </div>
  </nav>
</template>
