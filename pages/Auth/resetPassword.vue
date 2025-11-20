<template>
  <div
    class="w-screen min-h-screen bg-blue-100 flex items-center justify-center"
  >
    <div class="flex flex-col gap-[32px] h-[526px] w-[456px]">
      <div class="flex items-center justify-center">
        <img
          src="/assets/icons/Logo frame.png"
          alt=""
          class="w-[142px] h-[40px]"
        />
      </div>
      <div class="bg-white rounded-md h-[454px] py-[32px] px-[28px]">
        <div class="h-[390px] w-[400px] flex flex-col gap-[32px]">
          <div class="h-[94px] w-[400px] flex flex-col justify-between">
            <p class="font-semibold text-center text-[24px] bricolage">
              Reset Password
            </p>
            <p class="text-center text-gray-500 text-[16px] W-72">
              Enter a new password that would be used to access your Zenly
              account
            </p>
          </div>
          <div class="h-[264px] w-[400px] flex flex-col gap-[32px]">
            <div class="relative h-[80px] flex flex-col gap-[4px]">
              <p class="text-[14px] font-semibold">New Password</p>
              <input
                :type="showPassword ? 'text' : 'password'"
                class="border w-[400px] h-[56px] p-3 text-sm rounded-lg"
                placeholder="Enter Password"
              />
              <button
                type="button"
                @click="togglePassword"
                class="absolute right-3 top-2/4 text-gray-500 hover:text-gray-800"
              >
                <img
                  v-if="showPassword === true"
                  src="/eye-password-show-svgrepo-com.svg"
                  alt="Show"
                  class="w-5"
                />
                <img
                  v-else
                  src="/eye-password-hide-svgrepo-com.svg"
                  alt="Hide"
                  class="w-5"
                />
              </button>
            </div>
            <div class="relative h-[80px] flex flex-col gap-[4px]">
              <p class="text-[14px] font-semibold">Confirm Password</p>
              <input
                :type="showConfimPassword ? 'text' : 'password'"
                class="border w-[400px] h-[56px] p-3 text-sm rounded-lg"
                placeholder="Enter Password"
              />
              <button
                type="button"
                @click="toggleConfirmPassword"
                class="absolute right-3 top-2/4 text-gray-500 hover:text-gray-800"
              >
                <img
                  v-if="showConfimPassword === true"
                  src="/eye-password-show-svgrepo-com.svg"
                  alt="Show"
                  class="w-5"
                />
                <img
                  v-else
                  src="/eye-password-hide-svgrepo-com.svg"
                  alt="Hide"
                  class="w-5"
                />
              </button>
            </div>
            <button
              class="font-semibold text-[16px] bg-[#2F7DD0] w-[400px] h-[40px] text-center text-white rounded-md"
            >
              Reset Password
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
definePageMeta({
  layout: false,
});
const showPassword = ref(false);
const showConfimPassword = ref(false);
const togglePassword = () => {
  showPassword.value = !showPassword.value;
};

const toggleConfirmPassword = () => {
  showConfimPassword.value = !showConfimPassword.value;
};

// const resetPassword = async () =>{
//   const {data , }

// }
</script>
