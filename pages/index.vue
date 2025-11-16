<template>
  <div class="min-h-screen bg-gray-50 flex flex-col">
    <div class="w-full border-b bg-white">
      <div
        class="container mx-auto px-6 py-4 flex justify-between items-center"
      >
        <img
          src="/assets/icons/Logo blue frame.png"
          alt="Zenly Logo"
          class="w-[150px]"
        />

        <div class="flex gap-4">
          <nuxt-link
            to="/Auth/login"
            class="px-4 py-2 rounded-lg text-blue-600 font-medium hover:bg-blue-100"
          >
            Log In
          </nuxt-link>

          <nuxt-link
            to="/Auth/adminSignup"
            class="px-4 py-2 rounded-lg bg-blue-600 text-white font-medium hover:bg-blue-700"
          >
            Sign Up
          </nuxt-link>
        </div>
      </div>
    </div>

    <div
      class="flex flex-col items-center justify-center flex-1 text-center px-6"
    >
      <h1 class="text-4xl md:text-6xl font-bold text-gray-900">
        Welcome to Zenly
      </h1>

      <p class="mt-4 text-xl text-gray-600 text-center">
        Manage your workflow, track your team, and access features that <br/> make 
        work simple and efficient.
      </p>

      <div class="mt-8 flex gap-4">
        <nuxt-link
          to="/Auth/adminSignup"
          class="px-6 py-3 rounded-xl bg-blue-600 text-white text-lg font-medium hover:bg-blue-700"
        >
          Get Started
        </nuxt-link>

        <nuxt-link
          to="/Auth/login"
          class="px-6 py-3 rounded-xl border border-blue-600 text-blue-600 text-lg font-medium hover:bg-blue-50"
        >
          Log In
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script setup></script>

<script setup>
definePageMeta({
  layout: false,
});
</script>
