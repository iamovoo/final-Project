<template>
 
    <div
      class="w-lvh min-h-screen bg-[#D7E6F6] flex items-center justify-center"
    >
      <div class="w-[456px] h-[598px]">
        <div class="my-4 flex items-center justify-center">
          <img
            src="/assets/icons/Logo frame.png"
            alt=""
            class="w-[142px] h-[40px]"
          />
        </div>
        <div
          class="bg-white p-4 rounded-[8px] w-[456px] h-[526px] py-[32px] px-[28px]"
        >
          <div class="w-[400px] h-[462px] flex flex-col gap-[32px]">
            <div class="h-[74px] flex justify-between flex-col">
              <!-- <div class="h-[50px]"> -->
              <h4 class="text-center font-semibold text-[28px] bricolage">
                Login
              </h4>
              <!-- </div> -->
              <div class="h-[24px]">
                <p class="text-center text-[16px] text-[#667185]">
                  Welcome back to zenly
                </p>
              </div>
            </div>
            <div class="h-[356px] flex flex-col gap-[32px]">
              <div class="py-4 w-[400px] h-[80px] flex gap-[4px] flex-col">
                <p class="text-[14px] font-semibold mb-1">Work Email</p>
                <input
                  type="email"
                  class="border w-[400px] p-[16px] rounded-[6px] text-sm h-[56px]"
                  placeholder="ovo@company.com"
                  v-model="email"
                />
              </div>

              <div
                class="relative w-[400px] h-[116px] flex flex-col gap-[16px]"
              >
                <div class="h-[80px] flex gap-[4px] flex-col">
                  <p class="text-[14px] font-semibold">Password</p>

                  <input
                    :type="showPassword ? 'text' : 'password'"
                    class="border w-[400px] p-[16px] rounded-[6px] text-sm h-[56px]"
                    placeholder="Enter Password"
                    v-model="password"
                  />

                  <button
                    type="button"
                    @click="togglePassword"
                    class="absolute right-4 top-1/3 text-gray-500 hover:text-gray-800"
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

                <p class="text-[14px] text-end">Forgot Password?</p>
              </div>

              <div class="flex gap-[15px] h-[24px]">
                <input class="w-[24px] h-[24px]" type="checkbox" />
                <p class="font-[500] text-[14px]">Remember me for 30 days</p>
              </div>

              <button
                class="font-semibold bg-[#2F7DD0] w-[400px] h-[40px] text-center text-white rounded-[4px]"
                @click="login"
              >
                Continue to Zenly
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>


  <!-- <div class="block md:hidden">
    <div class="w-lvh min-h-screen bg-white flex flex-col">
      <div
        class="w-[375px] h-[504px] flex flex-col items-center justify-center gap-[32px]"
      >
        <div class="flex items-center justify-center mt-[20px]">
          <img src="/assets/icons/blue.png" alt="" class="w-[83px] h-[24px]" />
        </div>
        <div class="bg-white w-[375px] h-[448px] px-[20px] gap-[36px]">
          <div class="w-[335px] h-[356px] flex flex-col gap-[32px]">
            <div class="h-[56px] flex gap-[4px] flex-col">
              <h4 class="text-center font-semibold text-[20px] bricolage">
                Login
              </h4>
              <div class="h-[24px]">
                <p class="text-center text-[16px] text-[#667185]">
                  Welcome back to zenly
                </p>
              </div>
            </div>
            <div class="w-[335px] h-[356px] flex flex-col gap-[32px]">
              <div class="w-[335px] h-[80px] flex gap-[4px] flex-col">
                <p class="text-[14px] font-semibold">Work Email</p>
                <input
                  type="email"
                  class="border w-[335px] p-[16px] rounded-[6px] text-sm h-[56px]"
                  placeholder="ovo@company.com"
                  v-model="email"
                />
              </div>

              <div
                class="relative w-[335px] h-[116px] flex flex-col gap-[16px]"
              >
                <div class="h-[80px] flex gap-[4px] flex-col">
                  <p class="text-[14px] font-semibold">Password</p>

                  <input
                    :type="showPassword ? 'text' : 'password'"
                    class="border w-[335px] p-[16px] rounded-[6px] text-sm h-[56px]"
                    placeholder="Enter Password"
                    v-model="password"
                  />

                  <button
                    type="button"
                    @click="togglePassword"
                    class="absolute right-3 top-1/3 text-gray-500 hover:text-gray-800"
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

                <p class="text-[14px] text-end">Forgot Password?</p>
              </div>

              <div class="flex gap-[15px] h-[24px]">
                <input
                  class="w-[24px] h-[24px] rounded-[4px]"
                  type="checkbox"
                />
                <p class="font-[500] text-[14px]">Remember me for 30 days</p>
              </div>

              <button
                class="font-semibold bg-[#2F7DD0] w-[335px] h-[40px] text-center text-white rounded-[4px]"
                @click="login"
              >
                Continue to Zenly
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div> -->
</template>
<script setup>
definePageMeta({
  layout: false,
});
const baseURL = useRuntimeConfig().public.baseURL;
const password = ref("");
const email = ref("");
const showPassword = ref(false);
const togglePassword = () => {
  showPassword.value = !showPassword.value;
};
const user = ref("");
const userDetails = useState("userDetails", () => "");
const userTeam = useCookie('userTeam',{default:()=>[]})
const login = async () => {
  const { data, error } = await useFetch(`${baseURL}/auth/sign-in`, {
    method: "POST",
    body: {
      email: email.value,
      password: password.value,
    },
  });
  if (data.value) {
    console.log(data.value);
    user.value = data.value;
    userDetails.value = user.value;
    localStorage.setItem("userDetails", JSON.stringify(userDetails.value));
    console.log(user.value);

    const team = data.value.user.team;
     userTeam.value = [data.value.user.team , data.value.user.role ]
    if (data.value.user.role === "admin") {
      navigateTo("/admin");
    } 
    else if ( data.value.user.role === "member" && data.value.user.team === team) {
      navigateTo(`/${team}/member`);
    } 
    else {
      navigateTo(`${team}/teamLead`);
    }
  } else console.error(error.value);
};
</script>
