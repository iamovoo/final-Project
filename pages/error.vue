<template>
  <div class="w-full min-h-screen relative flex justify-center items-center">
    <div class="w-[1324px] absolute top-[40px]">
      <div class="w-full flex justify-between items-center h-[40px]">
        <img
          src="/assets/icons/blue.png"
          alt="Zenly Logo"
          class="w-[96px] h-[27px]"
        />

        <div class="flex gap-4 h-full">
          <nuxt-link to="/Auth/adminSignup" class="">
            <div
              class="h-full w-[77px] rounded-[4px] text-blue-600 font-semibold text-[16px] hover:bg-blue-100 flex justify-center items-center"
            >
              Sign Up
            </div>
          </nuxt-link>

          <nuxt-link to="/Auth/login">
            <div
              class="h-full w-[77px] rounded-[4px] bg-blue-600 text-white font-semibold text-[16px] hover:bg-blue-700 flex justify-center items-center"
            >
              Log In
            </div>
          </nuxt-link>
        </div>
      </div>
    </div>
    <div class="w-[712px] h-[527px] flex flex-col items-center justify-between">
      <div class="w-full h-[335px]">
        <img src="/Team Member.png" alt="" class="w-[712px] h-[335px]" />
      </div>
      <div
        class="w-[338px] h-[152px] flex flex-col items-center justify-between"
      >
        <!-- <h1 class="text-6xl font-bold text-red-500">{{ error.statusCode }}</h1> -->
        <h1 class="text-[28px] font-medium text-black">Page not found</h1>
        <!-- <p class="text-xl mt-4">{{ error.message }}</p> -->
        <p class="text-lg text-gray-400 text-center">
          Sorry, but the page you were looking for <br/>
          could not be found
        </p>
        <nuxt-link to="/">
          <div
            class="w-[139px] h-[40px] flex justify-center items-center font-semibold bg-[#2F7DD0] text-white rounded-[4px]"
          >
            Back to Home
          </div>
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script setup>
definePageMeta({
  layout: false,
});

const props = defineProps({
  error: Object,
});
</script>
