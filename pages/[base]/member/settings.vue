<template>
  <div class="w-[1107px] h-[60px] border-b py-[16px] border-[#EDEDF0]">
    <p class="text-[20px] bricolage">Settings</p>
  </div>
  <div class="w-[1107px] h-[684px] flex flex-col gap-[36px]">
    <div class="w-[1107px] h-[203px] flex flex-col gap-[24px]">
      <div class="w-[1107px] h-[119px] bg-[#D7E6F6] rounded-[8px]"></div>
      <div class="w-[1107px] h-[60px]">
        <div class="w-[264px] h-[60px] flex gap-[20px] items-center">
          <div class="w-[60px] h-[60px] rounded-full">
            <img
              src="/avatar.png"
              alt=""
              class="w-[60px] h-[60px] rounded-full"
            />
          </div>
          <div class="w-[184px] h-[44px] flex flex-col justify-between">
            <p class="text-[#101928] text-[16px] DMSans600 font-semibold">
              {{fullname}}
            </p>
            <p class="text-[#475367] text-[14px] DMSans400">
              {{userEmail}}
            </p>
          </div>
        </div>
      </div>
    </div>
    <div class="w-[1107px] h-[257px] flex flex-col gap-[20px]">
      <div class="w-[1107px] h-[52px] py-[16px] px-[24px] flex bg-[#F9FAFB]">
        <img src="/assets/icons/User.png" alt="" class="w-[16px] h-[16px]" />
        <p class="text-[#667185] text-[14px] DMSans400 font-medium">
          Personal Information
        </p>
      </div>
      <div
        class="w-[1107px] h-[185px] py-[28px] px-[24px] border border-[#E4E7EC] rounded-[8px] flex flex-col gap-[24px]"
      >
        <div class="w-[1059px] h-[52px] flex gap-[8px]">
          <div class="w-[525.5px] h-[52px] flex flex-col gap-[8px]">
            <p class="text-[#667185] text-[14px] DMSans400 font-medium">
              First Name
            </p>
            <p class="text-[#101928] text-[16px] DMSans400 font-semibold">
              {{firstName}}
            </p>
          </div>
          <div class="w-[525.5px] h-[52px] flex flex-col gap-[8px]">
            <p class="text-[#667185] text-[14px] DMSans400 font-medium">
              Last Name
            </p>
            <p class="text-[#101928] text-[16px] DMSans400 font-semibold">
              {{lastName}}
            </p>
          </div>
        </div>
        <div class="w-[1059px] h-[52px] flex gap-[8px]">
          <div class="w-[525.5px] h-[52px] flex flex-col gap-[8px]">
            <p class="text-[#667185] text-[14px] DMSans400 font-medium">Role</p>
            <p class="text-[#101928] text-[16px] DMSans400 font-semibold uppercase">
              {{role}}
            </p>
          </div>
          <div class=" h-[52px] flex flex-col gap-[8px]">
            <p class="text-[#667185] text-[14px] DMSans400 font-medium">Team</p>
            <div class="text-[12px] DMSans400">
              <p
                class=" text-[12px] DMSans400 font-semibold  py-[4px] px-[10px] rounded-[16px] "
                :class="team === 'Design'? 'bg-[#F6EDF8] text-[#853C90] ': team === 'Engineering'? 'bg-blue-200 text-blue-700 ': 'bg-green-200 text-green-700 '"
              >
               {{team}}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="w-[1107px] h-[125px] flex flex-col gap-[20px]">
      <div class="w-[1107px] h-[52px] flex py-[16px] px-[24px] gap-[8px] bg-[#F9FAFB] rounded-[8px] items-center">
        <img src="/assets/icons/LockSimple.png" alt="" class=" w-[16px] h-[16px]">
        <p  class="text-[#667185] text-[14px] DMSans400 font-medium">Security</p>
      </div>
      <div  class="w-[1107px] h-[80px] flex py-[28px] px-[24px] gap-[8px] bg-[#F9FAFB] rounded-[8px] items-center">
       <p class="text-[#667185] text-[14px] DMSans400 font-medium">Password</p>
       <button @click="changePasswordBtn" class="text-[#2F7DD0] text-[12px]  border-[#ACCBEC] DMSans400 font-medium w-[120px] h-[24px] border rounded-[4px] flex justify-center items-center"> Change password</button>
      </div>
    </div>
    <div v-if="isChangePasswordClicked">
      <ChangePasswordModal @closeModal="closeChangePasswordModal" />
    </div>
  </div>
</template>
<script setup>
const userTeamDetails = useCookie("userTeamDetails");
// console.log(userTeamDetails.value);
const userEmail = userTeamDetails.value.user.email
const fullname = userTeamDetails.value.user.full_name
const team = userTeamDetails.value.user.team

const role = userTeamDetails.value.user.role
const firstName = fullname.split(' ')[0] || 'No First Name'
const lastName = fullname.split(' ')[1] || 'No Last Name'
const isChangePasswordClicked = ref(false)
const changePasswordBtn = ()=>{
isChangePasswordClicked.value = true
}
const closeChangePasswordModal =(value)=>{
isChangePasswordClicked.value = value
}
</script>
