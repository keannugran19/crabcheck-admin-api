<script setup>
import AppLogo from '@/components/AppLogo.vue'
import TextInput from '@/components/TextInput.vue'
</script>

<template>
  <div class="image h-screen w-screen bg-cover bg-center">
    <div class="flex items-center justify-center min-h-screen">
      <div class="w-full max-w-sm p-8 space-y-4 bg-white opacity-90 rounded-lg shadow-lg">
        <div class="flex items-center justify-center">
          <!-- <img src="./assets/images/crabLogo.png" width="80" height="80" /> -->
          <AppLogo class="h-80 w-80" />
        </div>

        <h1 class="text-3xl font-bold text-center black">LOGIN</h1>
        <h3 class="text-sm text-center text-gray-400">Welcome to the admin panel.</h3>
        <!-- Form -->
        <form @submit.prevent="" class="space-y-6">
          <!-- Email Input -->
          <div>
            <TextInput type="email" id="email" placeholder="Email" autocomplete="off" required />
          </div>

          <!-- Password Input -->
          <div>
            <TextInput
              type="password"
              id="password"
              placeholder="Password"
              autocomplete="off"
              required
            />
          </div>

          <!-- Submit Button -->
          <SubmitButton class="w-full py-5">Login</SubmitButton>
        </form>
      </div>
    </div>
  </div>
</template>

<style>
.image {
  background-image: url('./assets/images/loginbackground.png');
  height: 100vh;
  width: 100vw;
  background-size: cover;
  background-position: center;
}
</style>
