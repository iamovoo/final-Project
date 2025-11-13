<template>
  <div class="h-[508px] w-[460px] border flex flex-col">
    <div class="h-[76px] w-[460px] py-[20px] px-[32px]">
      <div class="h-[36px] w-[396px] flex items-center justify-between">
        <div class="h-[28px]">
          <h6 class="text-[20px] font-medium bricolage">Notifications</h6>
        </div>
        <div
          class="h-[36px] w-[36px] border border-[#F0F2F5] font-bold flex justify-center items-center"
          @click="closeNotification"
        >
          x
        </div>
      </div>
    </div>
    <div class="h-[432px] w-[460px] border-b-2 flex flex-col gap-[32px]">
      <div>
        <div
          class="h-[108px] w-[460px] py-[28px] px-[32px] flex flex-col gap-[8px]"
        >
          <div class="w-[396px] h-[24px] flex justify-between items-center">
            <p class="text-[16px] text-[#475367] font-semibold">
              New Team Member
            </p>
            <p class="text-[12px] text-[#98A2B3] DMSans500">8:00AM, Oct 21</p>
          </div>
          <div class="w-[396px] h-[24px] text-[#667185] text-[14px] DMSans400">
            Temitope Ige has joined the Design team.
          </div>
        </div>
        <div
          class="h-[108px] w-[460px] py-[28px] px-[32px] flex flex-col gap-[8px]"
        >
          <div class="w-[396px] h-[24px] flex justify-between items-center">
            <p class="text-[16px] text-[#475367] font-semibold">
              Team Member on Leave
            </p>
            <p class="text-[12px] text-[#98A2B3] DMSans500">8:00AM, Oct 21</p>
          </div>
          <div class="w-[396px] h-[24px] text-[#667185] text-[14px] DMSans400">
            Oluwaseun Adebayo is currently on leave.
          </div>
        </div>
        <div
          class="h-[108px] w-[460px] py-[28px] px-[32px] flex flex-col gap-[8px]"
        >
          <div class="w-[396px] h-[24px] flex justify-between items-center">
            <p class="text-[16px] text-[#475367] font-semibold">
              Gbenga Adeyemi is Burnt Out
            </p>
            <p class="text-[12px] text-[#98A2B3] DMSans500">8:00AM, Oct 21</p>
          </div>
          <div class="w-[396px] h-[24px] text-[#667185] text-[14px] DMSans400">
            Burnout Meter: {90%}.
          </div>
        </div>
      </div>
      <div class="h-[40px] w-[460px] flex justify-around">
        <button
          class="w-[186px] h-[40px] flex items-center border justify-center text-[#2F7DD0] font-semibold text-[16px] border-[#ACCBEC] rounded-[4px]"
        >
          Mark all as read
        </button>
        <button
        @click="showAllNotifiction"
          class="w-[186px] h-[40px] flex items-center justify-center bg-[#2F7DD0] font-semibold text-[16px] text-white border-[#ACCBEC] rounded-[4px]"
        >
          See all notifications
        </button>
      </div>
    </div>
  </div>
</template>
<script setup>
const emit = defineEmits(["closeNotification",'showAllNotifiction']);
const closeNotification = () => {
  emit("closeNotification", false);
};
const showAllNotifiction = () => {
  emit("showAllNotifiction", true);
};
</script>
