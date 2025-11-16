<template>
  <div
    class="h-[72px] w-[1107px] py-[16px] flex justify-between border-b items-center mb-[30px]"
  >
    <h4 class="text-[24px] bricolage text-[#101928] font font-medium">Teams</h4>

    <div class="flex gap-[16px]">
      <div
        class=" cursor-pointer w-[205px] h-[40px] border-[#2F7DD0] border rounded-[4px] font-semibold text-[16px] text-[#2F7DD0] flex justify-center items-center gap-[8px]"
      >
        <span
          ><img
            src="/assets/icons/BlueUserPlus.png"
            alt=""
            class="text-[#2F7DD0]"
        /></span>
        Invite New Member
      </div>
      <div
        class=" cursor-pointer w-[205px] h-[40px] bg-[#2F7DD0] rounded-[4px] font-semibold text-[16px] text-[#F9FAFB] flex justify-center items-center gap-[8px]"
      >
        <span><img src="/assets/icons/WhiteUsers.png" alt="" /></span> Create
        New Team
      </div>
    </div>
  </div>
  <div class="h-[664px] w-[1107px] flex flex-col gap-[36px]">
    <div class="h-[188px] w-[1107px] flex flex-col gap-[20px]">
      <div class="flex gap-[8px]">
        <h4 class="text-[20px] bricolage text-[#101928] font font-medium">
          Design Teams
        </h4>
        <nuxt-link to="/admin/teams/Design">
          <div
            class="w-[114px] h-[32px] border-[#2F7DD0] border rounded-[4px] font-semibold text-[14px] text-[#2F7DD0] flex justify-center items-center"
          >
            Manage team
          </div>
        </nuxt-link>
      </div>
      <div class="h-[136px] w-[1107px] flex justify-between">
        <div
          class="h-[132px] w-[353px] flex flex-col justify-between border p-[24px] rounded-[8px] border-[#E4E7EC]"
        >
          <p class="text-[#667185] text-[14px] font-medium DMSans500">
            Average burnout percentage
          </p>
          <div class="flex h-[18px] gap-[12px] w-[305px] border">
            <div class="flex h-[8px] w-[267px] rounded-[8px]"></div>
            <p class="font-semibold text-[12px] text-[#344054]">45%</p>
          </div>
        </div>
        <div
          class="h-[132px] w-[353px] flex flex-col justify-between border p-[24px] rounded-[8px] border-[#E4E7EC]"
        >
          <p class="text-[#667185] text-[14px] font-medium DMSans500">
            Team burnout status
          </p>
          <div
            class="bg-[#ECFDF3] w-fit  text-[#04802E] text-[12px] DMSans500 rounded-[16px] h-[25px] px-[8px] py-[2px] flex gap-[4px] items-center"
          >
            <span class="text-[30px] text-[#04802E]">&#8226;</span> Charged
          </div>
        </div>
        <div
          class="h-[132px] w-[353px] flex flex-col justify-between border p-[24px] rounded-[8px] border-[#E4E7EC]"
        >
          <div class="flex h-[24px] justify-between w-[305px] ">
            <p class="text-[#667185] text-[14px] font-medium DMSans500">
              Average burnout percentage
            </p>
            <div
              class=" cursor-pointer w-[59px] h-[24px] border-[#2F7DD0] border rounded-[4px] font-semibold text-[14px] text-[#2F7DD0] flex justify-center items-center"
            >
             Modify
            </div>
          </div>
          <p class="text-[#101928] text-[32px] font-bold DMSans500">
            120
          </p>
        </div>
      </div>
    </div>
        <div class="h-[200px] w-[1107px] flex flex-col gap-[20px]">
      <div class="flex gap-[8px]">
        <h4 class="text-[20px] bricolage text-[#101928] font font-medium">
          Engineering Team
        </h4>
        <nuxt-link to="/admin/teams/Engineering">
          <div
            class="w-[114px] h-[32px] border-[#2F7DD0] border rounded-[4px] font-semibold text-[14px] text-[#2F7DD0] flex justify-center items-center"
          >
            Manage team
          </div>
        </nuxt-link>
      </div>
      <div class="h-[136px] w-[1107px] flex justify-between">
        <div
          class="h-[132px] w-[353px] flex flex-col justify-between border p-[24px] rounded-[8px] border-[#E4E7EC]"
        >
          <p class="text-[#667185] text-[14px] font-medium DMSans500">
            Average burnout percentage
          </p>
          <div class="flex h-[18px] gap-[12px] w-[305px] border">
            <div class="flex h-[8px] w-[267px] rounded-[8px]"></div>
            <p class="font-semibold text-[12px] text-[#344054]">45%</p>
          </div>
        </div>
        <div
          class="h-[132px] w-[353px] flex flex-col justify-between border p-[24px] rounded-[8px] border-[#E4E7EC]"
        >
          <p class="text-[#667185] text-[14px] font-medium DMSans500">
            Team burnout status
          </p>
          <div
            class="bg-[#ECFDF3] w-fit  text-[#04802E] text-[12px] DMSans500 rounded-[16px] h-[25px] px-[8px] py-[2px] flex gap-[4px] items-center"
          >
            <span class="text-[30px] text-[#04802E]">&#8226;</span> Charged
          </div>
        </div>
        <div
          class="h-[132px] w-[353px] flex flex-col justify-between border p-[24px] rounded-[8px] border-[#E4E7EC]"
        >
          <div class="flex h-[24px] justify-between w-[305px] ">
            <p class="text-[#667185] text-[14px] font-medium DMSans500">
              Average burnout percentage
            </p>
            <div
              class=" cursor-pointer w-[59px] h-[24px] border-[#2F7DD0] border rounded-[4px] font-semibold text-[14px] text-[#2F7DD0] flex justify-center items-center"
            >
             Modify
            </div>
          </div>
          <p class="text-[#101928] text-[32px] font-bold DMSans500">
            100
          </p>
        </div>
      </div>
    </div>
        <div class="h-[200px] w-[1107px] flex flex-col gap-[20px]">
      <div class="flex gap-[8px]">
        <h4 class="text-[20px] bricolage text-[#101928] font font-medium">
          Growth Team
        </h4>
        <nuxt-link to="/admin/teams/Growth">
          <div
            class="w-[114px] h-[32px] border-[#2F7DD0] border rounded-[4px] font-semibold text-[14px] text-[#2F7DD0] flex justify-center items-center"
          >
            Manage team
          </div>
        </nuxt-link>
      </div>
      <div class="h-[136px] w-[1107px] flex justify-between">
        <div
          class="h-[132px] w-[353px] flex flex-col justify-between border p-[24px] rounded-[8px] border-[#E4E7EC]"
        >
          <p class="text-[#667185] text-[14px] font-medium DMSans500">
            Average burnout percentage
          </p>
          <div class="flex h-[18px] gap-[12px] w-[305px] border">
            <div class="flex h-[8px] w-[267px] rounded-[8px]"></div>
            <p class="font-semibold text-[12px] text-[#344054]">45%</p>
          </div>
        </div>
        <div
          class="h-[132px] w-[353px] flex flex-col justify-between border p-[24px] rounded-[8px] border-[#E4E7EC]"
        >
          <p class="text-[#667185] text-[14px] font-medium DMSans500">
            Team burnout status
          </p>
          <div
            class="bg-[#ECFDF3] w-fit  text-[#04802E] text-[12px] DMSans500 rounded-[16px] h-[25px] px-[8px] py-[2px] flex gap-[4px] items-center"
          >
            <span class="text-[30px] text-[#04802E]">&#8226;</span> Charged
          </div>
        </div>
        <div
          class="h-[132px] w-[353px] flex flex-col justify-between border p-[24px] rounded-[8px] border-[#E4E7EC]"
        >
          <div class="flex h-[24px] justify-between w-[305px] ">
            <p class="text-[#667185] text-[14px] font-medium DMSans500">
              Average burnout percentage
            </p>
            <div
              class=" cursor-pointer w-[59px] h-[24px] border-[#2F7DD0] border rounded-[4px] font-semibold text-[14px] text-[#2F7DD0] flex justify-center items-center"
            >
             Modify
            </div>
          </div>
          <p class="text-[#101928] text-[32px] font-bold DMSans500">
            110
          </p>
        </div>
      </div>
    </div>
  </div>

</template>
<script setup>

</script>
