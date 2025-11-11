<template>
  <div class="hidden md:block">
    <div class="backgroundLayout">
      <div class="overflow-hidden w-[600px] h-[1024px]">
        <img
          src="/assets/icons/Frame zenly.png"
          alt=""
          class="object-contain w-full h-full"
        />
      </div>
      <div class="relative">
        <div
          v-if="detailsSubmitted === false"
          class="w-[473px] h-[520px] flex flex-col gap-[32px] absolute top-[146px] left-[184px]"
        >
          <div class="h-[46px] flex flex-col justify-between">
            <div class="h-[32px]">
              <p class="text-start text-[24px] text-[#101928] bricolage">
                Get Started with Zenly
              </p>
            </div>
            <div class="flex gap-[8px] h-[4px] w-[200px]">
              <button class="h-[4px] w-[96px] border active"></button>
              <button class="h-[4px] w-[96px] border notActive"></button>
            </div>
          </div>
          <div class="h-[390px] w-[473px] flex flex-col gap-[36px]">
            <div class="w-[473px] h-[314px] flex flex-col gap-[31px]">
              <div class="h-[84px] w-[473] flex flex-col gap-[12px]">
                <p class="DMSans400 text-[14px]">
                  Work Email<span class="text-[#D42620]">*</span>
                </p>
                <div>
                  <input
                    type="email"
                    v-model="email"
                    name=""
                    id=""
                    class="border w-[473px] py-[14px] px-[12px]"
                    placeholder="Enter your Work Email"
                  />
                  <p class="text-red-700 text-[10px] font-semibold p-1">
                    {{ emailError }}
                  </p>
                </div>
              </div>
              <div class="h-[84px] w-[473px] flex flex-col gap-[12px]">
                <p class="DMSans400 text-[14px]">
                  Company Name<span class="text-[#D42620]">*</span>
                </p>
                <input
                  type="text"
                  name=""
                  required
                  id=""
                  class="border w-[473px] py-[14px] px-[12px]"
                  placeholder="Enter your Company Name"
                />
              </div>
              <div class="h-[84px] w-[473px] flex flex-col gap-[12px] relative">
                <p class="DMSans400 text-[14px]">
                  Create Password<span class="text-[#D42620]">*</span>
                </p>
                <input
                  :type="showPassword ? 'text' : 'password'"
                  required
                  v-model="password"
                  name=""
                  id=""
                  class="border w-[473px] py-[14px] px-[12px]"
                  placeholder="Enter your Password"
                />
                <div
                  class="absolute top-[48px] right-3"
                  @click="showPasswordBtn"
                >
                  <button v-if="showPassword === false">
                    <img
                      src="/assets/icons/eye-password-hide-svgrepo-com.svg"
                      alt=""
                      class="w-5"
                    />
                  </button>
                  <button v-else>
                    <img
                      src="/assets/icons/eye-password-show-svgrepo-com.svg"
                      alt=""
                      class="w-5"
                    />
                  </button>
                </div>
              </div>
            </div>
            <button
              @click="createAccSubmit"
              class="bg-[#2F7DD0] w-[473px] h-[40px] text-[16px] text-white rounded-[4px]"
            >
              Create Account
            </button>
          </div>
          <div class="flex gap-[4px] DMSans">
            <p class="text-[14px] text-[#1D2739] DMSans500">
              Already have an account?
            </p>
            <p class="DMSans500 text-[14px] text-[#2F7DD0]">Sign in</p>
          </div>
        </div>
        <div
          v-else
          class="w-[473px] h-[238px] flex flex-col gap-[32px] absolute top-[146px] left-[184px]"
        >
          <div class="h-[46px] flex flex-col justify-between">
            <div class="h-[32px]">
              <p class="text-start text-[24px] text-[#101928] bricolage">
                Verify your Email
              </p>
            </div>
            <div class="flex gap-[8px] h-[4px] w-[200px]">
              <button class="h-[4px] w-[96px] border active"></button>
              <button class="h-[4px] w-[96px] border active"></button>
            </div>
          </div>
          <div class="h-[108px] w-[473px] flex flex-col gap-[20px]">
            <div class="w-[473px] h-[48px]">
              <p class="text-start">
                An email with a verification link has been sent to<br />
                {{ email }}
              </p>
            </div>
            <button
              class="bg-[#2F7DD0] w-[473px] h-[40px] text-[16px] text-white rounded-[4px]"
            >
              Go to Mail
            </button>
          </div>
          <div class="flex gap-[4px] DMSans">
            <p class="text-[14px] text-[#1D2739] DMSans500">
              Already have an account?
            </p>
            <p class="DMSans500 text-[14px] text-[#2F7DD0]">Sign in</p>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div class="block md:hidden">
    <div v-if="detailsSubmitted === false">
      <div class="w-[375px] h-[560px] flex flex-col gap-[32px] mx-auto">
        <div class="mt-5 px-[20px]">
          <img
            src="/assets/icons/blue.png"
            alt=""
            class="w-[83px] h-[24px]"
          />
        </div>
        <div class="h-[504px] px-[22px] flex flex-col gap-[32px]">
          <div class="h-[46px] flex flex-col gap-[10px]">
            <div class="h-[32px]">
              <p class="text-start text-[24px] text-[#101928] bricolage">
                Get Started with Zenly
              </p>
            </div>
            <div class="flex gap-[8px] h-[4px] w-[200px]">
              <button class="h-[4px] w-[96px] border active"></button>
              <button class="h-[4px] w-[96px] border notActive"></button>
            </div>
          </div>
          <div class="h-[374px] w-[335px] flex flex-col gap-[32px]">
            <div class="w-[335px] h-[302px] flex flex-col gap-[31px]">
              <div class="h-[80px] w-[335px] flex flex-col gap-[12px]">
                <p class="DMSans400 text-[14px]">
                  Work Email<span class="text-[#D42620]">*</span>
                </p>
                <div>
                  <input
                    type="email"
                    v-model="email"
                    name=""
                    id=""
                    class="border w-[335px] py-[14px] px-[12px]"
                    placeholder="Enter your Work Email"
                  />
                  <p class="text-red-700 text-[10px] font-semibold p-1">
                    {{ emailError }}
                  </p>
                </div>
              </div>
              <div class="h-[80px] w-[335px] flex flex-col gap-[12px]">
                <p class="DMSans400 text-[14px]">
                  Company Name<span class="text-[#D42620]">*</span>
                </p>
                <input
                  type="text"
                  name=""
                  required
                  id=""
                  class="border w-[335px] py-[14px] px-[12px]"
                  placeholder="Enter your Company Name"
                />
              </div>
              <div class="h-[80px] w-[335px] flex flex-col gap-[12px] relative">
                <p class="DMSans400 text-[14px]">
                  Create Password<span class="text-[#D42620]">*</span>
                </p>
                <input
                  :type="showPassword ? 'text' : 'password'"
                  required
                  name=""
                  id=""
                  class="border w-[335px] py-[14px] px-[12px]"
                  placeholder="Enter your Password"
                />
                <div
                  class="absolute top-[48px] right-3"
                  @click="showPasswordBtn"
                >
                  <button v-if="showPassword === false">
                    <img
                      src="/assets/icons/eye-password-hide-svgrepo-com.svg"
                      alt=""
                      class="w-5"
                    />
                  </button>
                  <button v-else>
                    <img
                      src="/assets/icons/eye-password-show-svgrepo-com.svg"
                      alt=""
                      class="w-5"
                    />
                  </button>
                </div>
              </div>
            </div>
            <button
              @click="createAccSubmit"
              class="bg-[#2F7DD0] w-[335px] h-[40px] text-[16px] text-white rounded-[4px]"
            >
              Create Account
            </button>
          </div>
          <div class="flex gap-[4px] DMSans">
            <p class="text-[14px] text-[#1D2739] DMSans500">
              Already have an account?
            </p>
            <p class="DMSans500 text-[14px] text-[#2F7DD0]">Sign in</p>
          </div>
        </div>
      </div>
    </div>
    <div v-else>
      <div class="w-[375px] h-[294px] flex flex-col gap-[32px] mx-auto">
        <div class="mt-5 px-[20px]">
          <img
            src="/assets/icons/blue.png"
            alt=""
            class="w-[83px] h-[24px]"
          />
        </div>
        <div class="w-[375px] h-[238px] flex flex-col gap-[32px] px-[20px]">
          <div class="h-[46px] flex flex-col justify-between">
            <div class="h-[32px]">
              <p class="text-start text-[24px] text-[#101928] bricolage">
                Verify your Email
              </p>
            </div>
            <div class="flex gap-[8px] h-[4px] w-[200px]">
              <button class="h-[4px] w-[96px] border active"></button>
              <button class="h-[4px] w-[96px] border active"></button>
            </div>
          </div>
          <div class="h-[108px] w-[335px] flex flex-col gap-[20px]">
            <div class="w-[335px] h-[48px]">
              <p class="text-start text-[14px]">
                An email with a verification link has been sent to<br />
                {{ email }}
              </p>
            </div>
            <button
              class="bg-[#2F7DD0] w-[335px] h-[40px] text-[16px] text-white rounded-[4px]"
            >
              Go to Mail
            </button>
          </div>
          <div class="flex gap-[4px] DMSans">
            <p class="text-[14px] text-[#1D2739] DMSans500">
              Already have an account?
            </p>
            <p class="DMSans500 text-[14px] text-[#2F7DD0]">Sign in</p>
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
// const activePage =(page)=>{
//   if (page === 1){
//     'bg-[#2F7DD0]'
//   }
//     else if (page === 2){
//     'bg-[#2F7DD0]'
//   }
// }
const baseURL = useRuntimeConfig().public.baseURL
const detailsSubmitted = ref(false);
const showPassword = ref(false);
const email = ref("");
const password = ref('')
const emailError = ref("");
const showPasswordBtn = () => {
  showPassword.value = !showPassword.value;
};
const createAccSubmit = async () => {
  if (email.value.includes("@")) {
    detailsSubmitted.value = true;
  } else {
    email.value = "";
    emailError.value = "kindly insert a Correct Email";
    setTimeout(() => {
      emailError.value = "";
    }, 2000);
  }
};
</script>

<style>
.backgroundLayout {
  display: grid;
  grid-template-columns: 600px 840px;
}
.active {
  background-color: #2f7dd0;
}
.notActive {
  background-color: #d7e6f6;
}
</style>
