<template>
  <div
    class="w-[537px] h-[190px] bg-[#FFFFFF] rounded-[8px] flex flex-col gap-[16px]"
  >
    <div class="h-[86px] w-[537px] pb-[6px]">
      <div class="flex flex-col px-[32px] pt-[20px]">
        <div class="flex justify-between">
          <p class="text-[20px] text-[#101928] font-medium bricolage">
            Sign out of your account?
          </p>
          <div
            class="w-[36px] h-[36px] flex justify-center items-center font-bold"
            @click="closeSignoutModal"
          >
            x
          </div>
        </div>
        <p class="text-[14px] text-[#667185]">
          Are you sure you want to sign out?
        </p>
      </div>
      <div
        class="flex pt-[28px] px-[32px] pb-[36px] border-b-2 justify-center items-center gap-[24px]"
      >
        <button
          @click="closeSignoutModal"
          class="text-[#2F7DD0] border border-[#ACCBEC] font-semibold text-[16px] DMSans500 h-[40px] w-[224.5px] rounded-[4px] z-10"
        >
          Cancel
        </button>
        <button
          @click="signOut"
          class="text-white bg-[#DD524D] font-semibold text-[16px] DMSans500 h-[40px] w-[224.5px] rounded-[4px] z-10"
        >
          Yes, Sign out
        </button>
      </div>
    </div>
  </div>
</template>
<script setup>
const userTeamDetails = useCookie("userTeamDetails");

const emit = defineEmits(["closeSignoutModal"]);
const closeSignoutModal = () => {
  emit("closeSignoutModal", false);
};
const signOut = () => {
  userTeamDetails.value = null;
  localStorage.removeItem("userDetails");
  navigateTo("/");
};
</script>
