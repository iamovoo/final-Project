<template>
  <div
    class="h-[72px] w-[1107px] py-[16px] flex justify-between border-b items-center mb-[30px]"
  >
    <h4 class="text-[24px] bricolage text-[#101928] font font-medium">Teams</h4>

    <div class="flex gap-[16px]">
      <div
        class="cursor-pointer w-[205px] h-[40px] border-[#2F7DD0] border rounded-[4px] font-semibold text-[16px] text-[#2F7DD0] flex justify-center items-center gap-[8px]"
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
        class="cursor-pointer w-[205px] h-[40px] bg-[#2F7DD0] rounded-[4px] font-semibold text-[16px] text-[#F9FAFB] flex justify-center items-center gap-[8px]"
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
          <div class="w-full bg-gray-200 rounded overflow-hidden">
            <div
              :class="getBarColor(designPercentage)"
              class="p-1 text-center text-xs font-medium leading-none"
              :style="{ width: `${designPercentage}%` }"
            >
              {{ designPercentage }}%
            </div>
          </div>
        </div>
        <div
          class="h-[132px] w-[353px] flex flex-col justify-between border p-[24px] rounded-[8px] border-[#E4E7EC]"
        >
          <p class="text-[#667185] text-[14px] font-medium DMSans500">
            Team burnout status
          </p>
          <div
          :class="getStatusColor(designPercentage)"
            class=" w-fit  text-[12px] DMSans500 rounded-[16px] h-[25px] px-[8px] py-[2px] flex gap-[4px] items-center"
          >
            <span class="text-[30px] text-[#04802E]">&#8226;</span> {{getStatus(designPercentage)}}
          </div>
        </div>
        <div
          class="h-[132px] w-[353px] flex flex-col justify-between border p-[24px] rounded-[8px] border-[#E4E7EC]"
        >
          <div class="flex h-[24px] justify-between w-[305px]">
            <p class="text-[#667185] text-[14px] font-medium DMSans500">
              Team Burnout Limit
            </p>
            <div
              @click="modifyTeamBurnoutLimit('design')"
              class="cursor-pointer w-[59px] h-[24px] border-[#2F7DD0] border rounded-[4px] font-semibold text-[14px] text-[#2F7DD0] flex justify-center items-center"
            >
              Modify
            </div>
          </div>
          <p class="text-[#101928] text-[32px] font-bold DMSans500">
            {{ designLimit }}
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
          <div class="w-full bg-gray-200 rounded overflow-hidden">
            <div
              :class="getBarColor(engineeringPercentage)"
              class="p-1 text-center text-xs font-medium leading-none"
              :style="{ width: `${engineeringPercentage}%` }"
            >
              {{ engineeringPercentage }}%
            </div>
          </div>
        </div>
        <div
          class="h-[132px] w-[353px] flex flex-col justify-between border p-[24px] rounded-[8px] border-[#E4E7EC]"
        >
          <p class="text-[#667185] text-[14px] font-medium DMSans500">
            Team burnout status
          </p>
          <div
          :class="getStatusColor(engineeringPercentage)"
            class=" w-fit  text-[12px] DMSans500 rounded-[16px] h-[25px] px-[8px] py-[2px] flex gap-[4px] items-center"
          >
            <span class="text-[30px] ">&#8226;</span> {{getStatus(engineeringPercentage)}}
          </div>
        </div>
        <div
          class="h-[132px] w-[353px] flex flex-col justify-between border p-[24px] rounded-[8px] border-[#E4E7EC]"
        >
          <div class="flex h-[24px] justify-between w-[305px]">
            <p class="text-[#667185] text-[14px] font-medium DMSans500">
              Team Burnout Limit
            </p>
            <div
              @click="modifyTeamBurnoutLimit('engineering')"
              class="cursor-pointer w-[59px] h-[24px] border-[#2F7DD0] border rounded-[4px] font-semibold text-[14px] text-[#2F7DD0] flex justify-center items-center"
            >
              Modify
            </div>
          </div>
          <p class="text-[#101928] text-[32px] font-bold DMSans500">
            {{ engineeringLimit }}
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
          <div class="w-full bg-gray-200 rounded overflow-hidden">
            <div
              :class="getBarColor(growthPercentage)"
              class="p-1 text-center text-xs font-medium leading-none"
              :style="{ width: `${growthPercentage}%` }"
            >
              {{ growthPercentage }}%
            </div>
          </div>
        </div>
        <div
          class="h-[132px] w-[353px] flex flex-col justify-between border p-[24px] rounded-[8px] border-[#E4E7EC]"
        >
          <p class="text-[#667185] text-[14px] font-medium DMSans500">
            Team burnout status
          </p>
          <div
          :class="getStatusColor(growthPercentage)"
            class="bg-[#ECFDF3] w-fit text-[#04802E] text-[12px] DMSans500 rounded-[16px] h-[25px] px-[8px] py-[2px] flex gap-[4px] items-center"
          >
            <span class="text-[30px] text-[#04802E]">&#8226;</span> {{getStatus(growthPercentage)}}
          </div>
        </div>
        <div
          class="h-[132px] w-[353px] flex flex-col justify-between border p-[24px] rounded-[8px] border-[#E4E7EC]"
        >
          <div class="flex h-[24px] justify-between w-[305px]">
            <p class="text-[#667185] text-[14px] font-medium DMSans500">
              Team Burnout Limit
            </p>
            <div
              @click="modifyTeamBurnoutLimit('growth')"
              class="cursor-pointer w-[59px] h-[24px] border-[#2F7DD0] border rounded-[4px] font-semibold text-[14px] text-[#2F7DD0] flex justify-center items-center"
            >
              Modify
            </div>
          </div>
          <p class="text-[#101928] text-[32px] font-bold DMSans500">
            {{ growthLimit }}
          </p>
        </div>
      </div>
    </div>
  </div>
  <div v-if="isModifyBtnClicked">
    <ModifyBurnoutLimit @closeModal="closeModal" :teamId="teamId" />
  </div>
</template>
<script setup>
const userTeamDetails = useCookie("userTeamDetails");
console.log(userTeamDetails.value);
const baseURL = useRuntimeConfig().public.baseURL;
const engineering = ref();
const design = ref();
const growth = ref();
const designLimit = ref(null);
const growthLimit = ref(null);
const engineeringLimit = ref(null);
const designTotalMembers = ref(0);
const growthTotalMembers = ref(0);
const engineeringTotalMembers = ref(0);
const designPercentage = ref(0);
const growthPercentage = ref(0);
const engineeringPercentage = ref(0);
const teamId = ref("");
const isModifyBtnClicked = ref(false);
const allTeams = ref([]);

const modifyTeamBurnoutLimit = (team) => {
  isModifyBtnClicked.value = true;
  if (team === "design") {
    teamId.value = "9d221e52-952e-48bd-8cb3-ab31fceee060";
  } else if (team === "engineering") {
    teamId.value = "9d221e52-b9ba-4bf1-a94b-f606fda12640";
  } else {
    teamId.value = "9d221e52-bf09-4f3d-be39-82bd6fe3d921";
  }
};
const getBarColor = (percent) => {
  if (percent >= 95) return "bg-red-500";
  if (percent >= 80) return "bg-orange-400";
  return "bg-green-500";
};
const getStatusColor = (percent) => {
  if (percent >= 95) {
    return "bg-red-200 text-[#DC143C]";
  }
  if (percent >= 80) {
    return "bg-orange-200 text-[#FA9C1B]";
  }
  return "bg-green-200 text-[#04802E]";
};
const getStatus = (percent) => {
  if (percent >= 95) {
    return "Burnt Out";
  }
  if (percent >= 80) {
    return "Almost Burnt Out";
  }
  return "Charged";
};
const closeModal = (value) => {
  isModifyBtnClicked.value = value;
};
const { data: teams } = await useFetch(`${baseURL}/teams/all`);
allTeams.value = teams.value?.data;

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
    designLimit.value = design.value[0]?.burnout_limit.burnout_limit;
    growthLimit.value = growth.value[0]?.burnout_limit.burnout_limit;
    engineeringLimit.value = engineering.value[0]?.burnout_limit.burnout_limit;
    designTotalMembers.value =
      design.value[0]?.about_to_be_burnt_out +
      design.value[0]?.burnt_out +
      design.value[0]?.charged;
    designPercentage.value =
      ((design.value[0]?.about_to_be_burnt_out + design.value[0]?.burnt_out) /
        designTotalMembers.value) *
      100;
    engineeringTotalMembers.value =
      engineering.value[0]?.about_to_be_burnt_out +
      engineering.value[0]?.burnt_out +
      engineering.value[0]?.charged;
    engineeringPercentage.value =
      ((engineering.value[0]?.about_to_be_burnt_out +
        engineering.value[0]?.burnt_out) /
        engineeringTotalMembers.value) *
      100;
    growthTotalMembers.value =
      growth.value[0]?.about_to_be_burnt_out +
      growth.value[0]?.burnt_out +
      growth.value[0]?.charged;
    growthPercentage.value =
      ((growth.value[0]?.about_to_be_burnt_out + growth.value[0]?.burnt_out) /
        growthTotalMembers.value) *
      100;
    // console.log("engineer", engineering?.value[0]);
  }
});
</script>
