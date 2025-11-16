<template>
  <div
    class="h-[72px] w-[1107px] py-[16px] flex justify-between border-b items-center mb-[30px] pr-[26px]"
  >
    <div class="flex gap-[10px] h-[32px] items-center">
      <p class="text-[24px] bricolage text-[#667185] font font-medium">
        <nuxt-link to="/admin/teams">Teams</nuxt-link>
      </p>
      <img
        src="/assets/icons/CaretRight.png"
        alt=""
        class="w-[20px] h-[20px]"
      />
      <div class="text-[24px] bricolage text-[#101928] font font-medium">
        {{ id }}
      </div>
    </div>

    <div
      @click="openModifyBurnoutLimit"
      class="w-[218px] h-[40px] bg-[#2F7DD0] rounded-[4px] font-semibold text-[16px] text-[#F9FAFB] flex justify-center items-center"
    >
      Modify Burnout Limit
    </div>
  </div>
  <!-- <div class="w-[1107px] h-[1754px] flex flex-col gap-[36px]"> -->
  <div class="w-[1107px] h-[1754px] flex flex-col gap-[36px]">
    <div class="h-[476px] flex flex-col gap-[24px] w-[1107px]">
      <div class="h-[28px] font-medium text-[20px] bricolage">Team metrics</div>
      <div class="h-[424px] w-[1107px] flex gap-[24px]">
        <div class="w-[348px] h-[424px] pb-[24px] border">
          <div class="h-[296px] p-[24px] flex flex-col gap-[24px]">
            <p class="text-[16px] DMSans500 font-medium">Burnout Report</p>
            <div class="w-[200px] h-[200px] border flex self-center"></div>
          </div>
          <div class="w-[348px] h-[104] px-[24px] flex flex-col gap-[8px]">
            <div class="w-[300px] h-[20px] flex justify-between items-center">
              <div
                class="w-[158px] h-[20px] text-[#667185] text-[14px] DMSans400 flex gap-[4px] items-center"
              >
                <span class="text-[30px] text-[#04802E]">&#8226;</span>
                Charged
              </div>
              <div class="w-[89px] h-[20px]">58 members</div>
            </div>
            <div class="w-[300px] h-[20px] flex justify-between items-center">
              <div
                class="w-[163px] h-[20px] text-[#667185] text-[14px] DMSans400 flex gap-[4px] items-center"
              >
                <span class="text-[30px] text-[#E67F4C]">&#8226;</span> About to
                be Burnt Out
              </div>
              <div class="w-[89px] h-[20px]">58 members</div>
            </div>
            <div class="w-[300px] h-[20px] flex justify-between items-center">
              <div
                class="w-[156px] h-[20px] text-[#667185] text-[14px] DMSans400 flex gap-[4px] items-center"
              >
                <span class="text-[30px] text-[#667185]">&#8226;</span>
                Burnout Break
              </div>
              <div class="w-[89px] h-[20px]">58 members</div>
            </div>
            <div class="w-[300px] h-[20px] flex justify-between items-center">
              <div
                class="w-[156px] h-[20px] text-[#667185] text-[14px] DMSans400 flex gap-[4px] items-center"
              >
                <span class="text-[30px] text-[#D42620]">&#8226;</span> Burnt
                Out
              </div>
              <div class="w-[89px] h-[20px]">58 members</div>
            </div>
          </div>
        </div>
        <div
          class="w-[348px] h-[424px] p-[20px] border flex flex-col justify-between items-center"
        >
          <div class="w-full h-[76px] flex flex-col gap-[12px]">
            <div class="w-full h-[24px] flex flex-col gap-[12px]">
              <div class="w-full h-[24px] flex justify-between">
                <p class="text-[#1D2739] text-[16px] font-medium DMSans500">
                  Team Burnout Meter
                </p>
                <div
                  class="flex gap-[8px] h-[21px] w-[76px] rounded-[16px] justify-center items-center text-[#04802E] DMSans500 text-[12px] px-3 bg-[#ECFDF3]"
                >
                  <span class="text-[30px] text-[#04802E]">&#8226;</span>
                  Charged
                </div>
              </div>
              <p class="text-[#667185] text-[14px] DMSans400">
                The percentage of your progress <br />
                toward reaching your burnout limit.
              </p>
            </div>
          </div>
          <div class="w-[232.6px] h-[162.49px] border"></div>
        </div>
        <div
          class="w-[348px] h-[424px] p-[20px] border flex flex-col items-center justify-between"
        >
          <!-- <div class="w-full h-[96px] flex flex-col gap-[12px]"> -->
          <div class="w-full h-[96px] flex flex-col gap-[12px]">
            <div class="w-full h-[24px] flex justify-between">
              <p class="text-[#1D2739] text-[16px] font-medium DMSans500">
                Burnout Limit
              </p>
              <div
                class="h-[24px] w-[59px] border border-[#ACCBEC] rounded-[4px] flex justify-center items-center text-[#2F7DD0] DMSans500 text-[12px]"
              >
                Modify
              </div>
            </div>
            <p class="text-[#667185] text-[14px] DMSans400">
              This is the maximum number of points a <br />
              design team member is required to reach to go <br />on a burnout
              break.
            </p>
          </div>
          <!-- </div> -->
          <div class="border w-[306px] h-[76px]"></div>
        </div>
      </div>
    </div>
    <div class="flex gap-[64px] w-full h-[116px]">
      <div class="flex flex-col justify-between w-[513px] h-full pt-[20px]">
        <p class="text-[#101828] text-[20px] font-medium">Team members</p>
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
      </div>
      <div
        class="flex flex-col justify-between w-[401px] h-full py-[20px] border rounded-[8px] border-[#E4E7EC] px-[28px]"
      >
        <div class="flex flex-col justify-between w-full h-[76px]">
          <div class="flex justify-between h-[32px] items-center">
            <p class="text-[#101828] text-[20px] font-medium">Team Lead</p>
            <div
              class="border border-[#ACCBEC] rounded-[4px] text-[#2F7DD0] text-[14px] font-medium h-[32px] flex justify-center items-center w-[149px]"
            >
              Change Team Lead
            </div>
          </div>
          <div class="flex gap-[16px] items-center">
            <img
              src="/assets/css/avatar.png"
              alt=""
              class="rounded-full w-[36px] h-[36px]"
            />
            <p class="font-semibold text-[18px] text-[#344054] DMSans500">
              Bolaji Folarin
            </p>
          </div>
        </div>
      </div>
    </div>
    <div
      class="w-[1107px] h-[986px] flex flex-col gap-[8px] border border-[#E4E7EC]"
    >
      <table class="w-[1107px]">
        <tr class="border-b bg-[#F9FAFB]">
          <th
            class="text-[14px] w-[281px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
          >
            Name
          </th>
          <th
            class="text-[14px] w-[281px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
          >
            Burnout Status
          </th>
          <th
            class="text-[14px] w-[281px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
          >
            Last Burnout Date
          </th>
          <th
            class="text-[14px] w-[281px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
          >
            Tasks Completed
          </th>
          <th
            class="text-[14px] w-[281px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
          >
            On Leave?
          </th>
        </tr>
        <div>
          <tr class="border-b text-start">
            <td
              class="text-[14px] w-[281px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
            >
              Oluwaseun Adebayo
            </td>
            <td
              class="text-[14px] w-[281px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
            >
              <div
                class="flex gap-[8px] h-[21px] w-[76px] rounded-[16px] justify-center items-center text-[#04802E] DMSans500 text-[12px] px-3 bg-[#ECFDF3]"
              >
                <span class="text-[30px] text-[#04802E]">&#8226;</span>
                Charged
              </div>
            </td>
            <td
              class="text-[14px] w-[281px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
            >
              <div
                class="flex bg-[#F9FAFB] py-[4px] px-[8px] border items-center justify-center gap-[8px] w-[148px] h-[28px]"
              >
                <p class="text-[14px] DMSans500 text-[#667185]">
                  2nd August 2023
                </p>
                <img
                  src="/assets/icons/PencilSimpleLine.png"
                  alt=""
                  class="w-[]"
                />
              </div>
            </td>
            <td
              class="text-[14px] w-[281px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#667185]"
            >
              50
            </td>
            <td
              class="text-[14px] w-[281px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
            >
              <input type="checkbox" name="" id="" class="w-[16px] h-[16px]" />
            </td>
          </tr>
        </div>
      </table>
    </div>
    <div class="w-[1107px] h-[68px] flex justify-between pt-[12px] pb-[16px]">
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
  <!-- </div> -->
  <div v-if="isModifyBurnoutLimitClicked">
    <ModifyBurnoutLimit @closeModal="closeModifyBurnoutLimit" />
  </div>
  <div v-if="false">
    <ModifyLastBurnoutDayModal />
  </div>
</template>
<script setup>
const { id } = useRoute().params;
const IsFilterClicked = ref(false);
const filterClicked = () => {
  IsFilterClicked.value = !IsFilterClicked.value;
};
import ModifyBurnoutLimit from "~/components/ModifyBurnoutLimit.vue";
const isModifyBurnoutLimitClicked = ref(false);
const openModifyBurnoutLimit = () => {
  isModifyBurnoutLimitClicked.value = true;
};
const closeModifyBurnoutLimit = (value) => {
  isModifyBurnoutLimitClicked.value = value;
};
</script>
