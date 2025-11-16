<template>
  <div
    class="w-[1107px] h-[64px] py-[16px] border-b border-[#EDEDF0] mb-[49px]"
  >
    <p class="text-[#101928] text-[24px] font-medium bricolage">Team Members</p>
  </div>
  <div class="w-[1119px] h-[1130px] flex flex-col gap-[16px]">
    <div class="w-[1107px] h-[44px] flex gap-[12px]">
      <div
        class="w-[400px] h-[44px] py-[12px] px-[14px] relative flex gap-[8px] border rounded-[8px]"
      >
        <img src="/assets/icons/search.png" alt="" class="" />
        <input
          type="text"
          name=""
          id=""
          placeholder="Search"
          class="w-[380px] focus:outline-none"
        />
      </div>
      <div
        @click="filterClicked"
        class="w-[101px] h-[44px] border rounded-[8px] flex justify-center items-center relative"
      >
        Filter
        <div class="absolute left-0 top-[55px]" v-if="IsFilterClicked">
          <Filter />
        </div>
      </div>
    </div>
    <div class="w-[1119px] h-[986px] rounded-[8px] border border-[#E4E7EC]">
      <table>
        <tr
          class="bg-[#F9FAFB] text-[14px] text-[#475467] font-medium text-start"
        >
          <th class="w-[326px] h-[58px] text-start px-[20px] py-[12px]">
            Name
          </th>
          <th class="w-[326px] h-[58px] text-start px-[20px] py-[12px]">
            Burnout Status
          </th>
          <th class="w-[257px] h-[58px] text-start px-[20px] py-[12px]">
            Tasks Completed
          </th>
          <th class="w-[266px] h-[58px] text-start px-[20px] py-[12px]">
            On Leave ?
          </th>
        </tr>
        <tr class="border-b text-start">
          <td
            class="text-[14px] w-[326px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
          >
            Oluwaseun Adebayo
          </td>
          <td
            class="text-[14px] w-[326px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
          >
            <div
              class="flex gap-[8px] h-[21px] w-[76px] rounded-[16px] justify-center items-center text-[#04802E] DMSans500 text-[12px] px-3 bg-[#ECFDF3]"
            >
              <span class="text-[30px] text-[#04802E]">&#8226;</span>
              Charged
            </div>
          </td>
          <td
            class="text-[14px] w-[257px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#667185]"
          >
            50
          </td>
          <td
            class="text-[14px] w-[266px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
          >
            <input type="checkbox" name="" id="" class="w-[16px] h-[16px]" />
          </td>
        </tr>
      </table>
    </div>
    <div>
                <div
            class="w-[1119px] h-[68px] flex justify-between pt-[12px] pb-[16px]"
          >
            <button
              class="border rounded-[8px] px-[14px] py-[8px] w-[113px] h-[36px ] text-[14px] font-medium DMSans500 flex gap-[8px] items-center justify-center"
            >
              <div class="pb-[4px]">&larr;</div>
              Previous
            </button>
            <div class="w-[292px] h-[40px] border"></div>
            <button
              class="border rounded-[8px] px-[14px] py-[8px] w-[113px] h-[36px ] text-[14px] font-medium DMSans500 flex gap-[8px] items-center justify-center"
            >
              Next
              <div class="pb-[4px]">&rarr;</div>
            </button>
          </div>
    </div>
  </div>
</template>
<script setup>
const IsFilterClicked = ref(false);
const filterClicked = () => {
  IsFilterClicked.value = !IsFilterClicked.value;
};
</script>
