<script setup>
import { RouterLink } from 'vue-router'
import AppLogo from './AppLogo.vue'
import DashboardIcon from './icons/DashboardIcon.vue'
import ReportsIcon from './icons/ReportsIcon.vue'
import MappingIcon from './icons/MappingIcon.vue'
import LogoutIcon from './icons/LogoutIcon.vue'
import { ref } from 'vue'

// let isSidebarOpen = ref(true)

let currentUser = ref('keannugran@gmail.net')

let linkStyles =
  'flex items-center px-6 py-4 text-lg font-semibold text-gray-700 hover:bg-orange-400 hover:text-white'

// let selectedLink = 'bg-orange-400 text-white'
</script>

<template>
  <!-- Hamburger Menu Button (Mobile Only) -->
  <!-- <button
      @click="isSidebarOpen = !isSidebarOpen"
      class="fixed lg:hidden p-4 bg-gray-800 text-white z-50"
    >
      <svg
        class="w-6 h-6"
        fill="none"
        stroke="currentColor"
        viewBox="0 0 24 24"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M4 6h16M4 12h16m-7 6h7"
        ></path>
      </svg>
    </button> -->

  <!-- Side Navigation Bar -->
  <aside
    :class="{
      // 'translate-x-0': isSidebarOpen,
      // '-translate-x-full': !isSidebarOpen,
    }"
    class="fixed lg:sticky top-0 transform transition-transform duration-200 rounded-md ease-in-out w-58 bg-orange-100 text-white h-screen z-40"
  >
    <nav class="flex flex-col h-full">
      <!-- App Logo -->
      <div class="p-5">
        <AppLogo class="w-auto h-12" />
      </div>
      <!-- Routes -->
      <RouterLink to="/" :class="linkStyles">
        <span class="mr-3">
          <DashboardIcon />
        </span>
        Dashboard
      </RouterLink>
      <RouterLink to="/reports" :class="linkStyles">
        <span class="mr-3">
          <ReportsIcon />
        </span>
        Reports
      </RouterLink>
      <RouterLink to="/mapping" :class="linkStyles">
        <span class="mr-3">
          <MappingIcon />
        </span>
        Mapping
      </RouterLink>

      <div class="flex justify-center mt-auto mb-2">
        <p class="text-gray-700 text-sm">{{ currentUser }}</p>
      </div>
      <RouterLink to="/logout" :class="linkStyles">
        <span class="mr-3">
          <LogoutIcon />
        </span>
        Log Out
      </RouterLink>
    </nav>
  </aside>
  <!-- Overlay for Mobile (Closes Sidebar on Click) -->
  <!-- <div
    v-if="isSidebarOpen"
    @click="isSidebarOpen = false"
    class="fixed inset-0 bg-black bg-opacity-50 z-30 lg:hidden"
  ></div> -->
</template>

<style scoped>
nav a.router-link-exact-active {
  color: white;
  --tw-bg-opacity: 1;
  background-color: rgb(251 146 60 / var(--tw-bg-opacity, 1));
}
</style>
