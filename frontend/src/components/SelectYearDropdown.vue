<script setup>
import { ref } from 'vue'

// Define available years
const years = ref(['All', 2024, 2025, 2026, 2027])

// Track selected year
const selectedYear = ref('All')

// Track dropdown open state
const isOpen = ref(false)

// Toggle dropdown visibility
const toggleDropdown = () => {
  isOpen.value = !isOpen.value
}

// Select a year
const selectYear = (year) => {
  selectedYear.value = year
  isOpen.value = false // Close dropdown after selection
}
</script>

<template>
  <div class="relative inline-block w-30">
    <!-- Dropdown Button -->
    <button
      @click="toggleDropdown"
      class="w-full px-4 py-2 border-b-2 border-gray-400 text-gray-700 flex justify-between items-center"
    >
      {{ selectedYear }}
      <span class="ml-2">&#9662;</span>
      <!-- Dropdown arrow -->
    </button>

    <!-- Dropdown Menu -->
    <div
      v-if="isOpen"
      class="absolute mt-2 w-full bg-white border border-gray-300 rounded-md shadow-lg z-50"
    >
      <ul>
        <li
          v-for="year in years"
          :key="year"
          @click="selectYear(year)"
          class="px-4 py-2 hover:bg-gray-200 cursor-pointer"
        >
          {{ year }}
        </li>
      </ul>
    </div>
  </div>
</template>
