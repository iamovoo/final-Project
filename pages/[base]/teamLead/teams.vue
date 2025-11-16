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
        @click="burnoutLimitClicked"
        class="w-[218px] h-[40px] bg-[#2F7DD0] rounded-[4px] font-semibold text-[16px] text-[#F9FAFB] flex justify-center items-center"
      >
        Modify Burnout Limit
      </div>
      <div
        class="absolute top-[50px] left-[92px] z-10 shadow-md bg-[#FFFFFF] rounded-[8px]"
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
    <div class="h-[1698px] w-[1107px] flex flex-col gap-[32px]">
      <div class="h-[476px] flex flex-col gap-[24px] w-[1107px]">
        <div class="h-[28px] font-medium text-[20px] bricolage">
          Team metrics
        </div>
        <div class="h-[424px] w-[1107px] flex gap-[24px]">
          <div class="w-[348px] h-[424px] pb-[24px] border">
            <div class="h-[296px] p-[24px] flex flex-col gap-[24px]">
              <p class="text-[16px] DMSans500 font-medium">Burnout Report</p>
              <div class="flex items-center justify-center">
                <div class="w-[200px] h-[200px]"></div>
              </div>
            </div>
            <div class="w-[348px] h-[104px] px-[24px] flex flex-col gap-[8px]">
              <div class="w-[300px] h-[20px] flex justify-between items-center">
                <div
                  class="flex gap-[8px] h-[20px] items-center text-[#667185] DMSans500 text-[14px]"
                >
                  <span class="text-[30px] text-[#8ACC66]">&#8226;</span>
                  Charged
                </div>
                <p class="font-medium DMSans500 text-[14px] text-[#1D2739]">
                  58 members
                </p>
              </div>
              <div class="w-[300px] h-[20px] flex justify-between items-center">
                <div
                  class="flex gap-[8px] h-[20px] items-center text-[#667185] DMSans500 text-[14px]"
                >
                  <span class="text-[30px] text-[#E67F4C]">&#8226;</span> About
                  to be Burnt Out
                </div>
                <p class="font-medium DMSans500 text-[14px] text-[#1D2739]">
                  20 members
                </p>
              </div>
              <div class="w-[300px] h-[20px] flex justify-between items-center">
                <div
                  class="flex gap-[8px] h-[20px] items-center text-[#667185] DMSans500 text-[14px]"
                >
                  <span class="text-[30px] text-[#E4E7EC]">&#8226;</span>
                  Burnout Break
                </div>
                <p class="font-medium DMSans500 text-[14px] text-[#1D2739]">
                  8 members
                </p>
              </div>
              <div class="w-[300px] h-[20px] flex justify-between items-center">
                <div
                  class="flex gap-[8px] h-[20px] items-center text-[#667185] DMSans500 text-[14px]"
                >
                  <span class="text-[30px] text-[#D42620]">&#8226;</span> Burnt
                  Out
                </div>
                <p class="font-medium DMSans500 text-[14px] text-[#1D2739]">
                  6 members
                </p>
              </div>
            </div>
          </div>
          <div
            class="w-[373px] h-[424px] p-[20px] border flex flex-col items-center justify-between"
          >
            <div class="h-[72px] w-[333px] flex flex-col gap-[8px]">
              <div class="h-[24px] w-[333px] flex justify-between items-center">
                <p class="text-[14px] font-medium text-[#1D2739]">
                  Team Burnout Meter
                </p>
                <div
                  class="flex gap-[8px] h-[21px] w-[76px] rounded-[16px] justify-center items-center text-[#04802E] DMSans500 text-[12px] bg-[#ECFDF3]"
                >
                  <span class="text-[30px] text-[#04802E]">&#8226;</span>
                  Charged
                </div>
              </div>
              <div
                class="w-[252px] text-[#667185] text-[14px] DMSans500 text-start"
              >
                The percentage of your progress <br />
                toward reaching your burnout limit.
              </div>
            </div>
            <div class="w-[232.5870361328125px] h-[162.48806762695312px]"></div>
          </div>
          <div
            class="w-[346px] h-[424px] p-[20px] border justify-between flex flex-col"
          >
            <div class="h-[92px] w-[306px] flex flex-col gap-[8px]">
              <div class="h-[24px] w-[306px] flex items-center">
                <p class="text-[16px] font-medium text-[#1D2739]">
                  Team Burnout Meter
                </p>
              </div>
              <div
                class="w-[306px] text-[#667185] text-[14px] DMSans500 text-start"
              >
                This is the maximum number of points a <br />
                design team member is required to reach to go <br />
                on a burnout break.
              </div>
            </div>
            <div class="h-[76px] w-[306px] p-[24px] border"></div>
          </div>
        </div>
      </div>
      <div class="w-[1107px] h-[1190px] flex flex-col gap-[24px]">
        <h6 class="text-[20px] text-[#101828] font-medium">Team members</h6>
        <div
          class="w-[1107px] h-[1046] flex flex-col gap-[24px] rounded-[12px]"
        >
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
          <div class="w-[1107px] h-[986px] flex flex-col gap-[8px]  border border-[#E4E7EC]">
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
                    <input
                      type="checkbox"
                      name=""
                      id=""
                      class="w-[16px] h-[16px]"
                    />
                  </td>
                </tr>
              </div>
            </table>
          </div>
          <div
            class="w-[1107px] h-[68px] flex justify-between pt-[12px] pb-[16px]"
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
      <div v-if="false">
        <ModifyLeaveStatus />
      </div>
      <div v-if="isBurnoutlimitClicked">
        <ModifyBurnoutLimit @closeModal="closeModal" />
      </div>
      <div v-if="false">
        <ModifyLastBurnoutDayModal />
      </div>
    </div>

</template>
<script setup>
import { useToast } from "vue-toastification";
const toast = useToast();
import Filter from "~/components/Filter.vue";
const IsFilterClicked = ref(false);
const filterClicked = () => {
  IsFilterClicked.value = !IsFilterClicked.value;
};
const isBurnoutlimitClicked = ref(false);
const burnoutLimitClicked = () => {
  isBurnoutlimitClicked.value = true;
  console.log(isBurnoutlimitClicked.value);
};
const closeModal = (value) => {
  isBurnoutlimitClicked.value = value;
  console.log(value, isBurnoutlimitClicked.value);
};
const isDateClicked = ref(false);
const dateBtnClicked = () => {
  isDateClicked.value = !isDateClicked.value;
};
const { id } = useRoute().params;
</script>
