<template>
  <div
    class="fixed bg-[#00000040] top-0 bottom-0 right-0 left-0 flex justify-center items-center"
  >
    <div class="border bg-[#FFFFFF] w-[537px] h-[250px] rounded-[12px]">
      <div class="w-[537px] h-[146px] pt-[20px] px-[32px] pb-[6px]">
        <div class="w-[473px] flex flex-col gap-[4px] h-[120px]">
          <div class="flex justify-between">
            <p
              class="text-[#101928] text-[20px] font-medium flex justify-center items-center"
            >
              Modify leave status
            </p>
            <div
            @click="closeModal"
              class="font-bold w-[36px] h-[36px] flex justify-center items-center pb-[5px] border rounded-[4px] border-[#F0F2F5] "
            >
              x
            </div>
          </div>
          <div
            class="w-[473px] h-[84px] flex flex-col justify-between "
          >
            <p
              class="text-[#667185] font-medium text-[14px] DMSans500 text-start"
            >
              Please confirm this team member is truly on Annual Leave as this
              would <br />
              reset the Burnout Meter to 0%.
            </p>
            <p
              class="text-[#667185] font-medium text-[14px] DMSans500 text-start"
            >
              This action is not reversible.
            </p>
          </div>
        </div>
      </div>
      <div class="w-[537px] h-[104px] pt-[28px] px-[32px] pb-[36px]">
        <div class=" flex justify-between">
          <button class=" text-[16px] bg-[#FFFFFF] text-[#2F7DD0] font-semibold DMSans500 border border-[#ACCBEC] h-[40px] flex justify-center items-center w-[224.5px]">Cancel</button>
          <button class=" text-[16px] bg-[#2F7DD0] text-[#F9FAFB] font-semibold DMSans500 h-[40px] flex justify-center items-center w-[224.5px]">Yes, I understand</button>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
// const closeModal = ()
</script>
