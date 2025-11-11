<template>
  <div class="hidden md:block">
    <div
      class="w-lvh min-h-screen bg-[#D7E6F6] flex items-center justify-center"
    >
      <div class="w-[456px] h-[498px]">
        <div class="my-4 flex items-center justify-center">
          <img
            src="/assets/icons/Logo frame.png"
            alt=""
            class="w-[142px] h-[40px]"
          />
        </div>
        <div
          class="bg-white rounded-[8px] w-[456px] h-[426px] py-[32px] px-[28px]"
        >
          <div class="w-[400px] h-[362px] flex flex-col justify-between">
            <div class="h-[122px] flex justify-between flex-col gap-[14px]">
              <h4 class="text-center font-semibold text-[28px] bricolage">
                Accept Invite
              </h4>
              <div class="h-[74px]">
                <p class="text-center text-[16px] text-gray-500">
                  You've been invited to zenly by Ogunsanya Chizi.<br/> Create a
                  Password for bolajifolarin@checklearn.com<br />
                  to accept invite and continue zenly
                </p>
              </div>
            </div>
            <div class="h-[208px] flex flex-col gap-[32px]">
              <div
                class="relative w-[400px] h-[80px] flex flex-col gap-[16px]"
              >
                <div class="h-[80px] flex gap-[4px] flex-col">
                  <p class="text-[14px] font-semibold">Password</p>

                  <input
                    :type="showPassword ? 'text' : 'password'"
                    class="border w-[400px] p-[16px] rounded-[6px] text-sm h-[56px]"
                    placeholder="Enter Password"
                  />

                  <button
                    type="button"
                    @click="togglePassword"
                    class="absolute right-3 top-1/2 text-gray-500 hover:text-gray-800"
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

              </div>

              <div class="flex gap-[15px] h-[24px]">
                <input class="w-[24px] h-[24px]" type="checkbox" />
                <p class="font-[500] text-[14px]">Remember me for 30 days</p>
              </div>

              <button
                class="font-semibold bg-[#2F7DD0] w-[400px] h-[40px] text-center text-white rounded-[4px]"
              >
                Continue to Zenly
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="block md:hidden">
  <div
      class="w-lvh min-h-screen flex justify-center"
    >
      <div class="w-[456px] h-[498px] flex flex-col gap-[32px]">
        <div class=" flex items-center justify-center mt-5">
          <img
            src="/assets/icons/blue.png"
            alt=""
            class="w-[83px] h-[24px]"
          />
        </div>
          <div class="w-[375px] h-[372px] flex flex-col justify-between px-[20px]">
            <div class="h-[128px] flex justify-between flex-col gap-[4px]">
              <h4 class="text-center font-semibold text-[20px] bricolage">
                Accept Invite
              </h4>
              <div class="">
                <p class="text-center text-[16px] text-gray-500">
                  You've been invited to zenly by<br/> Ogunsanya Chizi. Create a
                  Password <br/>for bolajifolarin@checklearn.com
                  to<br/> accept invite and continue zenly
                </p>
              </div>
            </div>
            <div class=" w-[335px] h-[208px] flex flex-col gap-[32px]">
              <div
                class="relative w-[335px] h-[80px] flex flex-col gap-[16px]"
              >
                <div class="h-[80px] flex gap-[4px] flex-col">
                  <p class="text-[14px] font-semibold">Password</p>

                  <input
                    :type="showPassword ? 'text' : 'password'"
                    class="border w-[335px] p-[16px] rounded-[6px] text-sm h-[56px]"
                    placeholder="Enter Password"
                  />

                  <button
                    type="button"
                    @click="togglePassword"
                    class="absolute right-3 top-1/2 text-gray-500 hover:text-gray-800"
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

              </div>

              <div class="flex gap-[15px] h-[24px]">
                <input class="w-[24px] h-[24px]" type="checkbox" />
                <p class="font-[500] text-[14px]">Remember me for 30 days</p>
              </div>

              <button
                class="font-semibold bg-[#2F7DD0] w-[335px] h-[40px] text-center text-white rounded-[4px]"
              >
                Continue to Zenly
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
const togglePassword = () => {
  showPassword.value = !showPassword.value;
};
</script>
