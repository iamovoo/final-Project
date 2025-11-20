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
        v-model="filterBySearchInput"
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
              Cumulative Burnout Points
            </th>
            <th class="w-[266px] h-[58px] text-start px-[20px] py-[12px]">
              Burnout Meter
            </th>
            <th class="w-[266px] h-[58px] text-start px-[20px] py-[12px]">
              Burnout Breaks Taken
            </th>
            <th class="w-[266px] h-[58px] text-start px-[20px] py-[12px]">
              On Leave ?
            </th>
          </tr>
          <tr
            class="border-b text-start"
            v-for="members in filteredTeamMembersBySearch"
            :key="members.full_name"
          >
            <td
              class="text-[14px] w-[326px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
            >
              {{ members.full_name }}
            </td>
            <td
              class="text-[14px] w-[326px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
            >
              <div
                :class="
                  members.burnout_status === 'charged'
                    ? 'bg-[#ECFDF3] text-[#04802E]'
                    : members.burnout_status === 'About to be Burnt Out'
                      ? 'bg-orange-200 text-orange-700'
                      : members.burnout_status === 'Burnt Out'
                        ? 'bg-red-200 text-red-700'
                        : 'bg-gray-200 text-gray-700'
                "
                class="flex gap-[8px] h-[21px] w-[76px] rounded-[16px] justify-center items-center DMSans500 text-[12px] px-3"
              >
                <span class="text-[30px]">&#8226;</span>
                {{ members.burnout_status }}
              </div>
            </td>
            <td
              class="text-[14px] w-[257px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#667185]"
            >
              {{ members.number_of_done_tasks }}
            </td>
            <td
              class="text-[14px] w-[257px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#667185]"
            >
              {{ members.cumulative_burnout_point }}
            </td>
            <td
              class="text-[14px] w-[257px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#667185]"
            >
              {{ (members.cumulative_burnout_point / teamBurnOutLimit) * 100 }}
            </td>
            <td
              class="text-[14px] w-[257px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#667185]"
            >
              {{ members.burnout_breaks_taken }}
            </td>
            <td
              class="text-[14px] w-[266px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
            >
              <input
                v-model="members.on_leave"
                type="checkbox"
                name=""
                id=""
                class="w-[16px] h-[16px]"
                disabled
              />
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
const baseURL = useRuntimeConfig().public.baseURL;
const IsFilterClicked = ref(false);
const filterClicked = () => {
  IsFilterClicked.value = !IsFilterClicked.value;
};
const userTeamDetails = useCookie("userTeamDetails");
const team = ref(userTeamDetails.value.user.team);
const id = ref(userTeamDetails.value.user.id);
const teamId = ref(null);
const teamMembers = ref([]);
const userData = ref();
const teamBurnOutLimit = ref();
const { data: user } = await useFetch(`${baseURL}/users/${id.value}`, {
  method: "get",
  headers: {
    Authorization: `Bearer ${userTeamDetails.value.access_token}`,
  },
});
userData.value = user.value;
// console.log(userData.value);
teamId.value = userData.value?.teams[0]?.id;
const { data: members } = await useFetch(
  `${baseURL}/teams/members/${teamId.value}`
);
teamMembers.value = members.value?.data
const { data, error } = await useFetch(`${baseURL}/teams/${teamId.value}`);
teamBurnOutLimit.value = data.value?.burnout_limit.burnout_limit;
// });
const filterBySearchInput = ref("");
const filteredTeamMembersBySearch = ref([]);
watchEffect(() => {
  if (filterBySearchInput.value !== "" && teamMembers?.value?.length !== 0) {
    filteredTeamMembersBySearch.value = teamMembers.value.filter((member) => {
      return member?.full_name
        ?.toLowerCase()
        .includes(filterBySearchInput.value.toLowerCase());
    });
  } else return (filteredTeamMembersBySearch.value = teamMembers.value);
});
</script>
