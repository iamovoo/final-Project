<template>
  <div
    class="w-[245px] h-[376px] p-[20px] border z-10 border-[#E4E7EC] bg-[#FFFFFF] rounded-[8px] flex flex-col gap-[20px]"
  >
    <div class="w-[205px] h-[174px] flex flex-col gap-[20px]">
      <div class="flex justify-between w-[205px] h-[18px]">
        <p class="text-[#98A2B3] text-[12px]">BURNOUT STATUS</p>
        <img src="/assets/icons/CaretDown.png" alt="" />
      </div>
      <div class="h-[178px] w-[205px]">
        <div class="h-[32px] w-[205px] flex justify-between items-start">
          <p class="text-[#667185] text-[14px]">Charged</p>
          <input type="checkbox" name="" id="" class="w-[16px] h-[16px]" />
        </div>
        <div class="h-[32px] w-[205px] flex justify-between items-start">
          <p class="text-[#667185] text-[14px]">Almost Burnout</p>
          <input type="checkbox" name="" id="" class="w-[16px] h-[16px]" />
        </div>
        <div class="h-[32px] w-[205px] flex justify-between items-start">
          <p class="text-[#667185] text-[14px]">Burnout</p>
          <input type="checkbox" name="" id="" class="w-[16px] h-[16px]" />
        </div>
        <div class="h-[32px] w-[205px] flex justify-between items-start">
          <p class="text-[#667185] text-[14px]">Burnout Break</p>
          <input type="checkbox" name="" id="" class="w-[16px] h-[16px]" />
        </div>
      </div>
    </div>
    <div class="w-[205px] h-[86px] flex flex-col gap-[12px]">
      <div class="flex justify-between w-[205px] h-[18px]">
        <p class="text-[#98A2B3] text-[12px]">LEAVE STATUS</p>
        <img src="/assets/icons/CaretDown.png" alt="" />
      </div>
      <div class="h-[56px] w-[205px] flex flex-col gap-[12px]">
        <div class="h-[32px] w-[205px] flex justify-between items-start">
          <p class="text-[#667185] text-[14px]">On leave</p>
          <input type="checkbox" name="" id="" class="w-[16px] h-[16px]" />
        </div>
        <div class="h-[32px] w-[205px] flex justify-between items-start">
          <p class="text-[#667185] text-[14px]">Not on leave</p>
          <input type="checkbox" name="" id="" class="w-[16px] h-[16px]" />
        </div>
      </div>
    </div>
    <button
      class="bg-[#2F7DD0] w-[205px] h-[40px] font-medium text-[14px] text-[#F9FAFB] flex justify-center items-center rounded-[4px]"
    >
      Apply Filter
    </button>
  </div>
</template>
