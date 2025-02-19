<script setup>
let model = defineModel({
  value: String,
})
</script>

<template>
  <input
    v-model="model"
    class="w-full px-4 py-3 mt-1 text-gray-900 bg-orange-200 rounded-xl focus:outline-none focus:ring-2 focus:ring-orange-500"
  />
</template>
