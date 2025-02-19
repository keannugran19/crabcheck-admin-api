<script setup>
import { ref } from 'vue'

// add variable to store background image path
defineProps({
  image: String,
})

let randomNumber = Math.floor(Math.random() * 100)
// make count dynamic to receive data from backend
let count = ref(randomNumber)
</script>

<template>
  <!-- Info Card -->
  <div
    class="relative bg-gray-200 rounded-b-lg overflow-hidden h-30 flex items-center justify-center"
  >
    <!-- Dark Overlay -->
    <img
      v-if="image"
      :src="image"
      alt="card-image"
      class="absolute brightness-50 bg-cover bg-center"
    />

    <!-- Centered Content -->
    <div class="relative text-center">
      <p class="font-medium"><slot /></p>
      <p class="text-3xl font-semibold">{{ count }}</p>
    </div>
  </div>
</template>
