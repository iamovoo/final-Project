<template>
  <div class="w-[1107px] h-[60px] border-b py-[16px] border-[#EDEDF0] mb-[40px]">
    <p
      class="text-[24px] bricolage text-[#101928] bricolage font-medium "
    >
      Help and Support
    </p>
  </div>
  <div
    class="w-[669px] h-[688px] border-b py-[16px] border-[#EDEDF0] flex gap-[24px] flex-col"
  >
    <p class="text-[#667185] text-[16px] DMSans400 text-start">
      Please fill the form below to place your request. We will get back to you
      as quickly <br />
      as possible to address your inquiry.
    </p>

    <div
      class="w-[605px] h-[612px] flex flex-col gap-[20px] py-[28px] px-[24px] border rounded-[8px] border-[#E4E7EC]"
    >
      <div class="w-[557px] h-[488px] flex flex-col gap-[24px]">
        <div class="w-[557px] h-[84px] flex gap-[36px]">
          <div class="w-[260.5px] h-[84px] flex flex-col justify-between">
            <p class="text-[14px] text-[#475367] DMSans400">
              First Name <span class="text-[#D42620]">*</span>
            </p>
            <input
              type="text"
              name=""
              id=""
              class="bg-[#F9FAFB] rounded-[6px] py-[14px] px-[16px] focus:outline-none"
              :placeholder="`${firstName}`"
              disabled
            />
          </div>
          <div class="w-[260.5px] h-[84px] flex flex-col justify-between">
            <p class="text-[14px] text-[#475367] DMSans400">
              Last Name <span class="text-[#D42620]">*</span>
            </p>
            <input
              type="text"
              name=""
              id=""
              class="bg-[#F9FAFB] rounded-[6px] py-[14px] px-[16px] focus:outline-none"
              :placeholder="`${lastName}`"
              disabled
            />
          </div>
        </div>
        <div class="w-[557px] h-[84px] flex gap-[36px]">
          <div class="w-[260.5px] h-[84px] flex flex-col justify-between">
            <p class="text-[14px] text-[#475367] DMSans400">
              Work Email <span class="text-[#D42620]">*</span>
            </p>
            <input
              type="email"
              name=""
              id=""
              class="bg-[#F9FAFB] rounded-[6px] py-[14px] px-[16px] focus:outline-none"
              :placeholder="`${userEmail}`"
              disabled
            />
          </div>
          <div class="w-[260.5px] h-[84px] flex flex-col justify-between">
            <p class="text-[14px] text-[#475367] DMSans400">
              Team <span class="text-[#D42620]">*</span>
            </p>
            <input
              type="text"
              name=""
              id=""
              class="bg-[#F9FAFB] rounded-[6px] py-[14px] px-[16px] focus:outline-none"
              :placeholder="`${team}`"
              disabled
            />
          </div>
        </div>
        <div class="w-[557px] h-[272px] flex gap-[10px] flex-col">
            <p class="text-[14px] text-[#475367] DMSans400">
              Message <span class="text-[#D42620]">*</span>
            </p>
            <textarea name="" id=""  class="rounded-[6px] py-[18px] px-[16px] focus:outline-none h-[240px] w-[557px] border border-[#D0D5DD]" placeholder="Enter your request here" v-model="requestArea"></textarea>
        </div>
      </div>
       <button @click="submitRequest" class=" w-[557px] h-[40px] text-[#F9FAFB] font-semibold text-[16px] DMSans500" 
        :disabled="!requestArea"
        :class="!requestArea? 'bg-[#D0D5DD]': 'bg-[#2F7DD0] active:bg-opacity-85'">Submit Request</button>
    </div>
  </div>
</template>
<script setup>
import { useToast } from 'vue-toastification';

const toast = useToast()
const requestArea = ref('')
const submitRequest = ()=>{
  if(requestArea){
    requestArea.value = ''
   toast.success('Support Request Sent')
  }
}
const userTeamDetails = useCookie("userTeamDetails");
// console.log(userTeamDetails.value);
const userEmail = userTeamDetails.value.user.email
const fullname = userTeamDetails.value.user.full_name
const team = userTeamDetails.value.user.team
const firstName = fullname.split(' ')[0]
const lastName = fullname.split(' ')[1]
// console.log(firstName,lastName);
</script>
