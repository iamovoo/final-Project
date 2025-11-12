<template>
  <!-- <div class="hidden md:block"> -->
  <div
    class="fixed bg-[#00000040] top-0 left-0 right-0 bottom-0 flex justify-center items-center"
  >
    <div class="bg-white w-[553px] h-[424px] py-[20px] px-[24px] flex flex-col gap-[28px] items-center rounded-[8px]">
      <!-- <div class="h-[390px] w-[400px] flex flex-col gap-[32px] justify-center"> -->
        <div class="h-[92px] w-[485px] flex flex-col justify-between">
          <div class="h-[36px] w-[485px] flex justify-between">
            <p
              class="font-semibold text-center text-[20px] bricolage text-[#1D2739]"
            >
              Change Password
            </p>
            <div
              @click="closeModal"
              class=" w-[36px] h-[36px] flex justify-center items-center pb-[5px] border rounded-[4px] border-[#F0F2F5] font-bold"
            >
              x
            </div>
          </div>
          <p class="text-start text-[#667185] text-[16px]">
           Enter a new password that would be used to access your Zenly <br/> 
           account
          </p>
        </div>
        <div class="h-[264px] w-[485px] flex flex-col gap-[32px]">
          <div class="relative h-[80px] w-[485px] flex flex-col gap-[4px]">
            <p class="text-[14px] font-medium DMSans500">New Password</p>
            <input
            v-model="NewPassword"
              :type="showPassword ? 'text' : 'password'"
              class="border w-[485px] h-[56px] p-3 text-sm rounded-lg"
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
          <div class="relative h-[80px] w-[485px] flex flex-col gap-[4px]">
            <p class="text-[14px] font-medium DMSans500">Confirm New Password</p>
            <input
            v-model="ConfirmNewPassword"
              :type="showConfimPassword ? 'text' : 'password'"
              class="border w-[485px] h-[56px] p-3 text-sm rounded-lg"
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
          @click="ResetPassword"
            class="font-semibold text-[16px] bg-[#2F7DD0] w-[485px] h-[40px] text-center text-white rounded-md"
          >
            Reset Password
          </button>
        </div>
      <!-- </div> -->
    </div>
  </div>

  <!-- </div> -->
</template>
<script setup>
import { useToast } from 'vue-toastification';

const toast = useToast()
const ConfirmNewPassword = ref('')
const NewPassword = ref('')
const showPassword = ref(false);
const showConfimPassword = ref(false);
const togglePassword = () => {
  showPassword.value = !showPassword.value;
};

const toggleConfirmPassword = () => {
  showConfimPassword.value = !showConfimPassword.value;
};
const emit = defineEmits(['closeModal'])
const closeModal =()=>{
  emit('closeModal', false)
}
const ResetPassword = () => {
 if(ConfirmNewPassword.value && NewPassword){
  toast.success('Password Reset Successfully')
  closeModal()
 }
};

</script>
