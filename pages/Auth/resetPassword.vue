<template>
  <div class="hidden md:block">
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
                    src="/assets/icons/eye-password-show-svgrepo-com.svg"
                    alt="Show"
                    class="w-5"
                  />
                  <img
                    v-else
                    src="/assets/icons/eye-password-hide-svgrepo-com.svg"
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
                    src="/assets/icons/eye-password-show-svgrepo-com.svg"
                    alt="Show"
                    class="w-5"
                  />
                  <img
                    v-else
                    src="/assets/icons/eye-password-hide-svgrepo-com.svg"
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
  </div>
  <div class="block md:hidden">
    <div class="w-screen min-h-screen flex justify-center">
      <div class="h-[436px] w-[375px] flex flex-col gap-[32px]">
        <div class="flex items-center justify-center mt-5">
          <img
            src="/assets/icons/blue.png"
            alt=""
            class="w-[83px] h-[24px]"
          />
        </div>
        <div class="bg-white px-[20px] w-[375px] h-[380px] flex flex-col gap-[36px]">
          <div class="class h-[80px] flex flex-col justify-between">
            <p class="font-semibold text-center text-[20px] bricolage">Reset Password</p>
           <div class=" h-[48px]">
             <p class="text-center text-[#667185] text-[15px] h-[48px]">
              Enter the the new Password that would be used to <br/>access 
              your zenly account
            </p>
           </div>
          </div>
          <div class="w-[335px] h-[264px] flex flex-col gap-[32px]">
            <div class="relative flex flex-col gap-[4px] h-[80px]">
              <p class="text-[16px] font-semibold">New Password</p>
              <input
                :type="showPassword ? 'text' : 'password'"
                class="border w-[335px] h-[56px] p-3 text-sm rounded-lg"
                placeholder="Enter Password"
              />
              <button
                type="button"
                @click="togglePassword"
                class="absolute right-3 top-2/4 text-gray-500 hover:text-gray-800"
              >
                <img
                  v-if="showPassword === true"
                  src="/assets/icons/eye-password-show-svgrepo-com.svg"
                  alt="Show"
                  class="w-5"
                />
                <img
                  v-else
                  src="/assets/icons/eye-password-hide-svgrepo-com.svg"
                  alt="Hide"
                  class="w-5"
                />
              </button>
            </div>
            <div class="relative flex flex-col gap-[4px] h-[80px]">
              <p class="text-[16px] font-semibold">Confirm Password</p>
              <input
                :type="showConfimPassword ? 'text' : 'password'"
                class="border w-[335px] h-[56px] p-3 text-sm rounded-[6px]"
                placeholder="Enter Password"
              />
              <button
                type="button"
                @click="toggleConfirmPassword"
                class="absolute right-3 top-2/4 text-gray-500 hover:text-gray-800"
              >
                <img
                  v-if="showConfimPassword === true"
                  src="/assets/icons/eye-password-show-svgrepo-com.svg"
                  alt="Show"
                  class="w-5"
                />
                <img
                  v-else
                  src="/assets/icons/eye-password-hide-svgrepo-com.svg"
                  alt="Hide"
                  class="w-5"
                />
              </button>
            </div>
            <button
              class="font-semibold text bg-blue-500 h-[40px] w-[335px] text-center text-white rounded-md"
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
