<template>
  <!-- Info Card -->
  <div
    class="relative bg-gray-200 rounded-b-lg border-t-4 border-gray-500 overflow-hidden h-30 flex items-center justify-center"
    style="
      background-image: url('your-image.jpg');
      background-size: cover;
      background-position: center;
    "
  >
    <!-- Dark Overlay -->
    <div class="absolute inset-0 bg-black opacity-60"></div>

    <!-- Centered Content -->
    <div class="relative text-white text-center">
      <p class="text-lg font-semibold">Total</p>
      <p class="text-2xl font-bold">20</p>
    </div>
  </div>
</template>
