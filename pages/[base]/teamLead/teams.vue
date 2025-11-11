<template>
  <div
    class="h-[72px] w-[1107px] py-[16px] flex justify-between border-b items-center mb-[30px] pr-[26px]"
  >
    <div class="flex gap-[20px]">
      <p class="text-[24px] bricolage">Teams</p>
      <div
        @click="dateBtnClicked"
        class="py-[4px] px-[8px] w-[88px] h-[28px] rounded-[2px] flex items-center gap-[4px] text-[#F9FAFB] border border-[#E4E7EC]"
      >
        <img
          src="/assets/icons/CalendarBlank.png"
          alt=""
          class="w-[12px] h-[12px]"
        />
        <p class="border-none DMSans500 text-[14px] text-[#667185]">Today</p>
        <img
          src="/assets/icons/CaretDown.png"
          alt=""
          class="w-[12px] h-[12px]"
        />
      </div>
    </div>

    <div
      class="w-[218px] h-[40px] bg-[#2F7DD0] rounded-[4px] font-semibold text-[16px] text-[#F9FAFB] flex justify-center items-center"
    >
      Modify Burnout Limit
    </div>
    <div
      class="absolute top-[50px] left-[138px] z-10 shadow-md bg-[#FFFFFF] rounded-[8px]"
      v-if="isDateClicked"
    >
      <div
        class="w-[240px] h-[200px] border py-[6px] px-[10px] z-10 bg-[#FFFFFF] rounded-[8px]"
      >
        <div class="w-[220px] h-[188px] py-[4px]">
          <div class="h-[36px] w-[240px] py-[8px] px-[16px]">
            <p class="text-[14px] DMSans400">Today</p>
          </div>
          <div class="h-[36px] w-[240px] py-[8px] px-[16px]">
            <p class="text-[14px] DMSans400">Last 7 Days</p>
          </div>
          <div class="h-[36px] w-[240px] py-[8px] px-[16px]">
            <p class="text-[14px] DMSans400">Last 30 Days</p>
          </div>
          <div class="h-[36px] w-[240px] py-[8px] px-[16px]">
            <p class="text-[14px] DMSans400">Last 3 Month</p>
          </div>
          <div class="h-[36px] w-[240px] py-[8px] px-[16px]">
            <p class="text-[14px] DMSans400">Last 12 Month</p>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="h-[1698px] w-[1107px]">
    <div class="h-[476px] flex flex-col gap-[24px] w-[1107px]">
      <div class="h-[28px] font-medium text-[20px] bricolage">Team metrics</div>
      <div class="h-[424px] w-[1107px] flex gap-[24px]">
        <div class="w-[348px] h-[424px] pb-[24px] border">
          <div class="h-[296px] p-[24px] flex flex-col gap-[24px]">
            <p class="text-[16px] DMSans500 font-medium">Burnout Report</p>
            <div class="w-[200px] h-[200px]"></div>
          </div>
          <div class="w-[348px] h-[104px] px-[24px] flex flex-col gap-[8px]">

          </div>
        </div>
        <div class="w-[348px] h-[424px] pb-[24px] border">
          <!-- <div class="h-[296px] p-[24px]"></div> -->
        </div>
        <div class="w-[348px] h-[424px] pb-[24px] border">
          <!-- <div class="h-[296px] p-[24px]"></div> -->
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
const {id} = useRoute().params
</script>
