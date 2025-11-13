<template>
  <div
    class="w-[1107px] h-[64px] py-[16px] border-b border-[#EDEDF0] mb-[49px]"
  >
    <p class="text-[#101928] text-[24px] font-medium bricolage">Dashboard</p>
  </div>
  <div class="w-[1119px] h-[1196px]">
    <div class="w-[1115px] h-[362px] flex flex-col gap-[24px]">
      <div class="w-[1115px] h-[28px] text-[20px] text-[#101828]">
        Burnout Metrics
      </div>
      <div
        class="w-[1115px] h-[310px] text-[20px] text-[#101828] flex gap-[20px]"
      >
        <div
          class="w-[392px] h-[310px] text-[20px] text-[#101828] flex flex-col gap-[16px] rounded-[8px] border p-[20px]"
        >
          <div
            class="w-[352px] h-[37px] flex justify-between items-start border-b"
          >
            <p class="text-[#667185] text-14px DMSans400">Team</p>
            <div
              class="bg-[#F6EDF8] text-[#853C90] text-[12px] DMSans500 rounded-[16px] h-[25px] px-[10px] py-[4px]"
            >
              Design
            </div>
          </div>
          <div
            class="w-[352px] h-[32px] flex justify-between items-start border-b"
          >
            <p class="text-[#667185] text-14px DMSans400">Last Burnout Date</p>
            <p class="text-[#1D2739] text-14px DMSans400">09th Sept, 2024</p>
          </div>
          <div
            class="w-[352px] h-[32px] flex justify-between items-start border-b"
          >
            <p class="text-[#667185] text-14px DMSans400">
              Cumulative Burnout Points
            </p>
            <p class="text-[#1D2739] text-14px DMSans400">120</p>
          </div>
          <div
            class="w-[352px] h-[32px] flex justify-between items-start border-b"
          >
            <p class="text-[#667185] text-14px DMSans400">Breaks Taken</p>
            <p class="text-[#1D2739] text-14px DMSans400">120</p>
          </div>
          <div
            class="w-[352px] h-[32px] flex justify-between items-start border-b"
          >
            <p class="text-[#667185] text-14px DMSans400">Tasks Completed</p>
            <p class="text-[#1D2739] text-14px DMSans400">4</p>
          </div>
          <div class="w-[352px] h-[25px] flex justify-between items-start">
            <p class="text-[#667185] text-14px DMSans400">Leave Status</p>
            <div
              class="bg-[#FEF3CD] text-[#967403] text-[12px] DMSans500 rounded-[16px] h-[25px] px-[10px] py-[4px] flex gap-[4px] items-center"
            >
              <span class="text-[30px] text-[#967403]">&#8226;</span> Due for
              leave
            </div>
          </div>
        </div>
        <div
          class="w-[373px] h-[310px] text-[20px] text-[#101828] flex gap-[16px] rounded-[8px] border p-[20px]"
        >
          <div class="h-[73px] w-[333px] flex flex-col justify-between items-center">
            <div class="h-[24px] w-[333px] flex justify-between items-center">
              <p class="text-[16px] font-medium text-[#1D2739]">
                Burnout Meter
              </p>
              <div
                class="flex gap-[8px] h-[21px] px-[8px] py-[2px] rounded-[16px] justify-center items-center text-[#B34C19] DMSans500 text-[12px] bg-[#FCEFE9]"
              >
                <span class="text-[30px] text-[#B34C19]">&#8226;</span>
                Almost Burnt Out
              </div>
            </div>
            <p class="text-[#667185] text-[]">The percentage of your progress toward reaching your burnout limit.</p>
          </div>
        </div>
        <div
          class="w-[310px] h-[310px] text-[20px] text-[#101828] flex gap-[16px] rounded-[8px] border"
        ></div>
      </div>
    </div>
  </div>
</template>
