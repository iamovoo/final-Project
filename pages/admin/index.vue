<template>
  <div
    class="h-[64px] w-[1171px] py-[16px] flex gap-[20px] border-b items-center mb-[30px]"
  >
    <p class="text-[24px] bricolage">Dashboard</p>
    <!-- <div class="relative">
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
      <div
        v-if="isDateClicked"
        class="absolute top-[45px] shadow-md bg-[#FFFFFF] rounded-[8px]"
      >
        <DateModal />
      </div>
    </div> -->
  </div>

  <div class="w-[1107px] h-[1241px] flex flex-col gap-[36px]">
    <div class="h-[192px] w-[1107px] gap-[20px] flex flex-col">
      <div class="w-[1107px] h-[40px] flex justify-between">
        <p class="text-[20px] font-medium text-[#101928] bricolage">Overview</p>
        <div
          @click="inviteMembers"
          class="w-[205px] h-[40px] text-[16px] flex justify-center items-center font-semibold text-[#F9FAFB] bg-[#2F7DD0] gap-[8px] rounded-[4px]"
        >
          <img
            src="/assets/icons/UserPlus.png"
            alt=""
            class="w-[16px] h-[16px]"
          />Invite New Member
        </div>
      </div>
      <div class="h-[132px] w-[1107px] gap-[20px] flex">
        <div
          class="w-[258.75px] h-[132px] border p-[24px] rounded-[8px] flex flex-col gap-[24px]"
        >
          <p class="text-[#667185] text-[14px] font-medium">
            Total work members
          </p>
          <div class="w-[210.75px] h-[40px] flex justify-between">
            <p class="font-bold text-[32px] text-[#101928]">
              {{ totalMembers }}
            </p>
            <div
              class="w-[40px] h-[40px] overflow-hidden p-[10px] border-[#E4E7EC] rounded-full border"
            >
              <img
                src="/assets/icons/Users.png"
                alt=""
                class="object-contain w-[20px] h-[20px]"
              />
            </div>
          </div>
        </div>
        <div
          class="w-[258.75px] h-[132px] border p-[24px] rounded-[8px] flex flex-col gap-[24px]"
        >
          <p class="text-[#667185] text-[14px] font-medium">Members on Leave</p>
          <div class="w-[210.75px] h-[40px] flex justify-between">
            <p class="font-bold text-[32px] text-[#101928]">
              {{ totalMembersOnLeave }}
            </p>
            <div
              class="w-[40px] h-[40px] overflow-hidden p-[10px] border-[#E4E7EC] rounded-full border"
            >
              <img
                src="/assets/icons/blueUsers.png"
                alt=""
                class="object-contain w-[20px] h-[20px]"
              />
            </div>
          </div>
        </div>
        <div
          class="w-[258.75px] h-[132px] border p-[24px] rounded-[8px] flex flex-col gap-[24px]"
        >
          <p class="text-[#667185] text-[14px] font-medium">
            Appraoching Burnout
          </p>
          <div class="w-[210.75px] h-[40px] flex justify-between">
            <p class="font-bold text-[32px] text-[#101928]">
              {{ totalMembersApproachingBurnout }}
            </p>
            <div
              class="w-[40px] h-[40px] overflow-hidden p-[10px] border-[#E4E7EC] rounded-full border"
            >
              <img
                src="/assets/icons/orangeUsers.png"
                alt=""
                class="object-contain w-[20px] h-[20px]"
              />
            </div>
          </div>
        </div>
        <div
          class="w-[258.75px] h-[132px] border p-[24px] rounded-[8px] flex flex-col gap-[24px]"
        >
          <p class="text-[#667185] text-[14px] font-medium">Burnt Out</p>
          <div class="w-[210.75px] h-[40px] flex justify-between">
            <p class="font-bold text-[32px] text-[#101928]">
              {{ totalMembersOfBurntout }}
            </p>
            <div
              class="w-[40px] h-[40px] overflow-hidden p-[10px] border-[#E4E7EC] rounded-full border"
            >
              <img
                src="/assets/icons/redUsers.png"
                alt=""
                class="object-contain w-[20px] h-[20px]"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="w-[1107px] h-[566px] flex flex-col gap-[36px]">
      <div class="w-[1107px] h-[152px] flex gap-[24px]">
        <div
          class="w-[502px] h-[152px] flex flex-col justify-between pt-[20px] px-[30px] pb-[26px] bg-[#2F7DD0] rounded-[8px]"
        >
          <p class="font-semibold text-[18px] text-[#667185] DMSans500">
            Average Burnout Percentage
          </p>
          <p class="font-bold text-[32px] text-[#F9FAFB] DMSans500">
            {{ AverageBurnOutPercentage }}%
          </p>
          <div class="w-[442px] h-[5px] rounded-[4px] bg-[#F9FAFB]"></div>
        </div>
        <div
          class="w-[581px] h-[152px] flex border justify-between pt-[20px] px-[30px] pb-[26px] rounded-[8px]"
        >
          <div
            class="w-[154.3333282470703px] h-[106px] flex flex-col justify-between rounded-[8px]"
          >
            <p class="font-medium text-[14px] text-[#667185] DMSans500">
              Design
            </p>
            <p
              :class="
                designBurnoutMeter < 80
                  ? 'text-green-500'
                  : designBurnoutMeter >= 80 && designBurnoutMeter < 95
                    ? 'text-[#FA9C1B]'
                    : designBurnoutMeter >= 95 && designBurnoutMeter < 100
                      ? 'text-[#DC143C]'
                      : 'text-[#DCDCDC]'
              "
              class="font-bold text-[32px] DMSans500"
            >
              {{ designBurnoutMeter }}%
            </p>
            <div class="w-full bg-gray-200 rounded overflow-hidden">
              <div
                :class="
                  designBurnoutMeter < 80
                    ? 'bg-green-500'
                    : designBurnoutMeter >= 80 && designBurnoutMeter < 95
                      ? 'bg-[#FA9C1B]'
                      : designBurnoutMeter >= 95 && designBurnoutMeter < 100
                        ? 'bg-[#DC143C]'
                        : 'bg-[#DCDCDC]'
                "
                class="p-1 text-center text-xs font-medium leading-none"
                :style="{ width: `${designBurnoutMeter}%` }"
              ></div>
            </div>
          </div>
          <div
            class="w-[154.3333282470703px] h-[106px] flex flex-col justify-between rounded-[8px]"
          >
            <p class="font-semibold text-[14px] text-[#667185] DMSans500">
              Engineering
            </p>
            <p
              :class="
                engineeringBurnoutMeter < 80
                  ? 'text-green-500'
                  : engineeringBurnoutMeter >= 80 &&
                      engineeringBurnoutMeter < 95
                    ? 'text-[#FA9C1B]'
                    : engineeringBurnoutMeter >= 95 &&
                        engineeringBurnoutMeter < 100
                      ? 'text-[#DC143C]'
                      : 'text-[#DCDCDC]'
              "
              class="font-bold text-[32px] text-[#FA9C1B] DMSans500"
            >
              {{ engineeringBurnoutMeter }}%
            </p>
            <div class="w-full bg-gray-200 rounded overflow-hidden">
              <div
                :class="
                  engineeringBurnoutMeter < 80
                    ? 'bg-green-500'
                    : engineeringBurnoutMeter >= 80 &&
                        engineeringBurnoutMeter < 95
                      ? 'bg-[#FA9C1B]'
                      : engineeringBurnoutMeter >= 95 &&
                          engineeringBurnoutMeter < 100
                        ? 'bg-[#DC143C]'
                        : 'bg-[#DCDCDC]'
                "
                class="p-1 text-center text-xs font-medium leading-none"
                :style="{ width: `${engineeringBurnoutMeter}%` }"
              ></div>
            </div>
          </div>
          <div
            class="w-[154.3333282470703px] h-[106px] flex flex-col justify-between rounded-[8px]"
          >
            <p class="font-semibold text-[14px] text-[#667185] DMSans500">
              Growth
            </p>
            <p
              :class="
                growthBurnoutMeter < 80
                  ? 'text-green-500'
                  : growthBurnoutMeter >= 80 && growthBurnoutMeter < 95
                    ? 'text-[#FA9C1B]'
                    : growthBurnoutMeter >= 95 && growthBurnoutMeter < 100
                      ? 'text-[#DC143C]'
                      : 'text-[#DCDCDC]'
              "
              class="font-bold text-[32px] text-[#86DC3D] DMSans500"
            >
              {{ growthBurnoutMeter }}%
            </p>
            <div class="w-full bg-gray-200 rounded overflow-hidden">
              <div
                :class="
                  growthBurnoutMeter < 80
                    ? 'bg-green-500'
                    : growthBurnoutMeter >= 80 && growthBurnoutMeter < 95
                      ? 'bg-[#FA9C1B]'
                      : growthBurnoutMeter >= 95 && growthBurnoutMeter < 100
                        ? 'bg-[#DC143C]'
                        : 'bg-[#DCDCDC]'
                "
                class="p-1 text-center text-xs font-medium leading-none"
                :style="{ width: `${growthBurnoutMeter}%` }"
              ></div>
            </div>
          </div>
        </div>
      </div>
      <div class="w-[1107px] h-[378px] flex flex-col justify-between">
        <div class="w-[1107px] h-[28px] text-[#101928] font-medium text-[20px]">
          Burnout Distribution
        </div>
        <div
          class="w-[1107px] h-[326px] border rounded-[8px] border-[#E4E7EC] flex flex-col justify-between p-[24px]"
        >
          <div
            class="w-[1059px] h-[229px] border rounded-[8px] border-[#E4E7EC] grid grid-cols-3 gap-4"
          >
            <div class="border rounded-[8px] border-[#E4E7EC]">
              <ClientOnly>
                <BurnoutBarChart
                  teamName="Design"
                  :stats="barChart('Design')"
                />
              </ClientOnly>
            </div>
            <div class="border rounded-[8px] border-[#E4E7EC]">
              <ClientOnly>
                <BurnoutBarChart
                  teamName="Engineering"
                  :stats="barChart('Engineering')"
                />
              </ClientOnly>
            </div>
            <div class="border rounded-[8px] border-[#E4E7EC]">
              <ClientOnly>
                <BurnoutBarChart
                  teamName="Growth"
                  :stats="barChart('Growth')"
                />
              </ClientOnly>
            </div>
          </div>
          <div class="w-full h-[17px] border flex gap-4 items-center">
            <div
              class="flex gap-2 text-[12px] font-medium items-center text-[#667185]"
            >
              <div class="w-[10px] h-[10px] bg-[#86DC3D]"></div>
              Charged
            </div>
            <div
              class="flex gap-2 text-[12px] font-medium items-center text-[#667185]"
            >
              <div class="w-[10px] h-[10px] bg-[##DCDCDC]"></div>
              On Leave
            </div>
            <div
              class="flex gap-2 text-[12px] font-medium items-center text-[#667185]"
            >
              <div class="w-[10px] h-[10px] bg-[#FA9C1B]"></div>
              Approaching Burnout
            </div>
            <div
              class="flex gap-2 text-[12px] font-medium items-center text-[#667185]"
            >
              <div class="w-[10px] h-[10px] bg-[#DC143C]"></div>
              Burnt Out
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="w-[1107px] h-[411px] flex justify-between">
      <div class="w-[541.5px] h-[411px] flex flex-col justify-between">
        <div class="flex justify-between">
          <p class="font-medium text-[#101828] text-[20px]">Members on Leave</p>
          <!-- <div class="w-[316px] h-[40px] flex justify-end"> -->
          <button
            @click="openModal('on Leave', 'Members on Leave')"
            class="border-[#ACCBEC] text-[#2F7DD0] w-[115px] h-[40px] font-semibold flex items-center justify-center gap-[8px] rounded-[4px] border"
          >
            <img
              src="/assets/icons/ArrowUpRight.png"
              alt=""
              class="h-[16px] w-[16px]"
            />
            View all
          </button>
          <!-- </div> -->
        </div>
        <div
          class="w-[541.5px] h-[347px] p-[20px] flex flex-col gap-[14px] border-[#E4E7EC] rounded-[8px] border bg-[#FCFCFC] items-center relative overflow-hidden"
        >
          <div
            class="bg-white w-full h-full rounded-[8px] p-[10px] border border-[#E4E7EC] flex items-center flex-col"
          >
            <div
              v-if="allMembersOnLeave.length !== 0"
              class=" w-full h-full overflow-hidden"
            >
              <div
                v-for="member in allMembersOnLeave"
                class="w-full h-[60px] px-[19px] py-[7px] items-start flex justify-between bg-white border-b mb-[7px] "
              >
                <div class="flex gap-[4px]">
                  <img
                    src="/avatar.png"
                    alt=""
                    class="w-[46px] h-[46px] rounded-full"
                  />
                  <div
                    class="w-full h-[49px] flex flex-col items-start pl-[4px]"
                  >
                    <p class="text-[14px] text-[#667185] font-bold DMSans500">
                      {{ member?.full_name }}
                    </p>
                    <div class="text-[12px] DMSans400">
                      <p
                        class="text-[#853C90] text-[12px] DMSans400 font-semibold py-[4px] rounded-[16px] w-[58px]"
                      >
                        Member
                      </p>
                    </div>
                  </div>
                </div>
                <div
                  :class="getStatusColor(member?.burnout_status)"
                  class="text-[12px] DMSans500 rounded-[16px] h-[25px] px-[8px] py-[2px] flex gap-[4px] items-center"
                >
                  <span class="text-[30px]">&#8226;</span>
                  {{ member?.burnout_status }}
                </div>
              </div>
            </div>
            <div v-else class="absolute top-[50%]">
              <p class="text-gray-600 text-[14px]">No Members on Leave</p>
            </div>
          </div>
        </div>
      </div>
      <div class="w-[541.5px] h-[411px] flex flex-col justify-between">
        <div class="flex justify-between">
          <p class="font-medium text-[#101828] text-[20px]">Burnout Alerts</p>
          <!-- <div class="w-[316px] h-[40px] flex justify-end"> -->
          <button
            @click="openModal('Burnout', 'Burnout Alerts')"
            class="border-[#ACCBEC] text-[#2F7DD0] w-[115px] h-[40px] font-semibold flex items-center justify-center gap-[8px] rounded-[4px] border"
          >
            <img
              src="/assets/icons/ArrowUpRight.png"
              alt=""
              class="h-[16px] w-[16px]"
            />
            View all
          </button>
          <!-- </div> -->
        </div>
        <div
          class="w-[541.5px] h-[347px] p-[24px] flex flex-col gap-[14px] border-[#E4E7EC] rounded-[8px] border bg-[#FCFCFC] items-center relative overflow-hidden"
        >
          <div
            class="bg-white w-full h-full rounded-[8px] p-[10px] border border-[#E4E7EC] flex items-center flex-col"
          >
            <div
              v-if="allMembersBurntout.length !== 0"
              class="bg-white w-full h-full"
            >
              <div
                v-for="member in allMembersBurntout"
                class="w-[429.5px] h-[60px] px-[19px] py-[7px] items-start flex justify-between bg-white border-b mb-[7px]"
              >
                <div class="flex gap-[4px]">
                  <img
                    src="/avatar.png"
                    alt=""
                    class="w-[46px] h-[46px] rounded-full"
                  />
                  <div class="h-[49px] flex flex-col items-center">
                    <p class="text-[14px] text-[#667185] font-medium DMSans500">
                      {{ member?.full_name }}
                    </p>
                    <div class="text-[12px] DMSans400">
                      <p
                        class="text-[#853C90] text-[12px] DMSans400 font-semibold py-[4px] rounded-[16px] w-[58px]"
                      >
                        Member
                      </p>
                    </div>
                  </div>
                </div>
                <div
                  class="bg-red-200 text-red-700 text-[12px] DMSans500 rounded-[16px] h-[25px] px-[8px] py-[2px] flex gap-[4px] items-center"
                >
                  <span class="text-[30px] text-red-700">&#8226;</span>
                  {{ member?.burnout_status }}
                </div>
              </div>
            </div>
            <div v-else class="absolute top-[50%]">
              <p class="text-gray-400 text-[14px]">No Members Burntout</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div v-if="isInviteNewMember">
    <InviteNewMemberModal @closeModal="cancelInviteNewMemberModal" />
  </div>
  <div v-if="showModal">
    <onLeaveModal
      :title="title"
      :modalData="modalData"
      @closeModal="closeOnLeaveModal"
    />
  </div>
</template>
<script setup>
import { useToast } from "vue-toastification";
const toast = useToast();
// const userDetails = ref("");
const allTeams = ref([]);
const isInviteNewMember = ref(false);
const baseURL = useRuntimeConfig().public.baseURL;
const isDateClicked = ref(false);
const totalMembers = ref(0);
const totalMembersOnLeave = ref(0);
const totalMembersApproachingBurnout = ref(0);
const totalMembersOfBurntout = ref(0);
const engineeringBurnoutMeter = ref(0);
const designBurnoutMeter = ref(0);
const growthBurnoutMeter = ref(0);
const AverageBurnOutPercentage = ref(0);
const allMembersOnLeave = ref([]);
const allMembersBurntout = ref([]);
const modalData = ref([]);

// const dateBtnClicked = () => {
//   isDateClicked.value = !isDateClicked.value;
// };
const inviteMembers = () => {
  isInviteNewMember.value = true;
};
const cancelInviteNewMemberModal = (value) => {
  isInviteNewMember.value = value;
};
const userTeamDetails = useCookie("userTeamDetails");
// console.log(userTeamDetails.value);
const { data } = await useFetch(`${baseURL}/users/all`, {
  method: "get",
  headers: {
    Authorization: `Bearer ${userTeamDetails.value.access_token}`,
  },
});
// console.log(data.value);
watchEffect(() => {
  if (data.value) {
    totalMembers.value = data.value?.total;
  }
});
// console.log(totalMembers);
const { data: d } = await useFetch(
  `${baseURL}/teams/members/9d221e52-952e-48bd-8cb3-ab31fceee060?on_leave=true`
);

const { data: e } = await useFetch(
  `${baseURL}/teams/members/9d221e52-b9ba-4bf1-a94b-f606fda12640?on_leave=true`
);
const { data: g } = await useFetch(
  `${baseURL}/teams/members/9d221e52-bf09-4f3d-be39-82bd6fe3d921?on_leave=true`
);

// console.log("d", d.value);
// console.log("e", e.value);
// console.log("g", g.value);
watchEffect(() => {
  if (d.value?.data && e.value && g.value) {
    totalMembersOnLeave.value =
      d.value?.data.length + e.value?.data.length + g.value?.data.length;
    allMembersOnLeave.value = [
      ...(d.value?.data || []),
      ...(e.value?.data || []),
      ...(g.value?.data || []),
    ];
    // console.log(allMembersOnLeave.value);
  }
});
const { data: teams } = await useFetch(`${baseURL}/teams/all`);
allTeams.value = teams.value?.data;
const engineering = ref([]);
const growth = ref([]);
const design = ref([]);
const barChart = (team) => {
  if (team === "Engineering") {
    return {
      charged: engineering.value[0]?.charged,
      leave: e.value?.data.length,
      approching: engineering.value[0]?.about_to_be_burnt_out,
      burnt: engineering.value[0]?.burnt_out,
    };
  } else if (team === "Design") {
    return {
      charged: design.value[0]?.charged,
      leave: d.value?.data.length,
      approching: design.value[0]?.about_to_be_burnt_out,
      burnt: design.value[0]?.burnt_out,
    };
  } else {
    return {
      charged: growth.value[0]?.charged,
      leave: g.value?.data.length,
      approching: growth.value[0]?.about_to_be_burnt_out,
      burnt: growth.value[0]?.burnt_out,
    };
  }
};
const { data: designBurntOutMembers } = await useFetch(
  `${baseURL}/teams/members/9d221e52-952e-48bd-8cb3-ab31fceee060?status=burnt_out`
);

const { data: engineeringBurntOutMembers } = await useFetch(
  `${baseURL}/teams/members/9d221e52-b9ba-4bf1-a94b-f606fda12640?status=burnt_out`
);
const { data: growthBurntOutMembers } = await useFetch(
  `${baseURL}/teams/members/9d221e52-bf09-4f3d-be39-82bd6fe3d921?status=burnt_out`
);
// console.log(
//   growthBurntOutMembers.value?.data,
//   designBurntOutMembers.value?.data,
//   engineeringBurntOutMembers.value
// );
allMembersBurntout.value = [
  ...(growthBurntOutMembers?.value?.data || []),
  ...(designBurntOutMembers?.value?.data || []),
  ...(engineeringBurntOutMembers?.value?.data || []),
];

watchEffect(() => {
  if (allTeams.value) {
    engineering.value = allTeams.value?.filter((teams) => {
      return teams.name === "Engineering";
    });
    growth.value = allTeams.value?.filter((teams) => {
      return teams.name === "Growth";
    });
    design.value = allTeams.value?.filter((teams) => {
      return teams.name === "Design";
    });
    // console.log(Engineering,Growth,Design)
    totalMembersOfBurntout.value =
      engineering.value[0].burnt_out +
      design.value[0].burnt_out +
      growth.value[0].burnt_out;
    // console.log(totalMembersOfBurntout.value);
    totalMembersApproachingBurnout.value =
      engineering.value[0].about_to_be_burnt_out +
      design.value[0].about_to_be_burnt_out +
      growth.value[0].about_to_be_burnt_out;
    // console.log(totalMembersApproachingBurnout.value);

    engineeringBurnoutMeter.value =
      (engineering.value[0]?.burnt_out /
        engineering.value[0]?.burnout_limit?.burnout_limit) *
      100;
    designBurnoutMeter.value =
      (design.value[0]?.burnt_out /
        design.value[0]?.burnout_limit?.burnout_limit) *
      100;
    growthBurnoutMeter.value =
      (growth.value[0]?.burnt_out /
        growth.value[0]?.burnout_limit?.burnout_limit) *
      100;
    AverageBurnOutPercentage.value =
      growthBurnoutMeter.value +
      designBurnoutMeter.value +
      engineeringBurnoutMeter.value;
    // console.log(engineering.value);
    // console.log(engineeringBurnoutMeter.value);

    barChart();
  }
});
const showModal = ref(false);
const title = ref("");
const openModal = (data, titleName) => {
  showModal.value = true;
  title.value = titleName;
  //  console.log('hello',data)
  if (data === "on Leave") {
    modalData.value = allMembersOnLeave.value;
    // console.log(modalData.value,'on leave');
    return modalData.value;
  } else {
    modalData.value = allMembersBurntout.value;
    //  console.log(modalData.value);
    return modalData.value;
  }
};
const closeOnLeaveModal = (value) => {
  showModal.value = value;
};
const getStatusColor = (status) => {
  if (status == "Burnt out") {
    return "bg-red-200 text-[#DC143C]";
  }
  if (status == " almost Burnt out") {
    return "bg-orange-200 text-[#FA9C1B]";
  }
  return "bg-green-200 text-[#04802E]";
};
</script>
