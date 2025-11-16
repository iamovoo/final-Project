<!-- <template>
<p>{{ error }}</p>
</template>
<script setup >
const prop = defineProps({
  error: Object
})
console.log(error)
</script> -->

<template>
  <div
    class="min-h-screen flex flex-col items-center justify-center bg-gray-100"
  >
    <h1 class="text-6xl font-bold text-red-500">{{ error.statusCode }}</h1>
    <p class="text-xl mt-4">{{ error.message }}</p>

    <button
      @click="handleReload"
      class="mt-6 px-4 py-2 bg-blue-500 text-white rounded-lg"
    >
      Go Home
    </button>
  </div>
</template>

<script setup>
const props = defineProps({
  error: Object,
});

const handleReload = () => {
  clearError({ redirect: "/" });
};
</script>
