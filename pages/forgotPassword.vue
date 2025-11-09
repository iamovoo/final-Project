<template>
  <div class="hidden md:block">
    <div
      class="w-screen min-h-screen bg-blue-100 flex items-center justify-center"
    >
      <div class="w-[456px] h-[414px] flex flex-col gap-[32px]">
        <div class="flex items-center justify-center">
          <img
            src="/assets/icons/Logo frame.png"
            alt=""
            class="w-[142px] h-[40px]"
          />
        </div>
        <div
          class="bg-white p-4 rounded-md w-[456px] h-[342px] px-[28px] py-[32px]"
        >
          <div class="flex flex-col gap-[32px] h-[278px]">
            <div
              class="w-[400px] h-[94px] flex flex-col items-center justify-between"
            >
              <p class="font-semibold text-center text-[24px] bricolage">
                Forgot Password ?
              </p>
              <p class="text-center text-[#667185] text-[16px]">
                Enter the email linked to your Zenly account and we'd <br />
                send a link to reset your Password
              </p>
            </div>
            <div
              class="w-[400px] h-[152px] flex flex-col justify-between gap-[32px]"
            >
              <div class="h-[80px] flex flex-col gap-[4px]">
                <p class="text-xs font-semibold">Work Email</p>
                <input
                  type="email"
                  class="border w-[400px] p-3 text-sm rounded-lg h-[56px]"
                  placeholder="ovo@company.com"
                />
              </div>
              <button
                class="font-semibold text-xs bg-[#2F7DD0] h-[40px] w-[400px] text-center text-white rounded-md"
              >
                Continue
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div class="block md:hidden">
    <div class="w-lvh min-h-screen flex justify-center">
 
      <div class="h-[324px] w-[375px] flex flex-col gap-[32px] mt-5">
        <div class="flex items-center justify-center">
          <img
            src="/assets/icons/blue.png"
            alt=""
            class="w-[83px] h-[24px]"
          />
        </div>
        <div class="bg-white px-[20px] rounded-md h-[268px] flex flex-col gap-[32px]">
          <div class="h-[80px] w-[335px] flex flex-col justify-between">
            <p class="font-semibold text-center text-[20px] bricolage">
              Forgot Password ?
            </p>
            <p class="text-center text-gray-500 text-[16px] leading-[24px]">
              Enter the email linked to your Zenly account <br />
              and we'd send a link to reset your Password
            </p>
          </div>
          <div class="w-[335px] h-[152px] flex flex-col gap-[32px]">
            <div class="">
              <p class="text-[16px] font-semibold">Work Email</p>
              <input
                type="email"
                class="border w-[335px] p-3 text-sm rounded-lg h-[56px]"
                placeholder="ovo@company.com"
              />
            </div>
            <button
              class="font-semibold text-xs bg-[#2F7DD0] h-[40px]  w-[335px] text-center text-white rounded-md"
            >
              Continue
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

// const showPassword = ref(false);
// const togglePassword = () => {
//   showPassword.value = !showPassword.value;
// };
</script>
