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
            <div class="w-[200px] h-[200px] flex self-center">
              <div class="w-full h-full">
                <ClientOnly>
                  <DonutChart :value="getData()" />
                </ClientOnly>
              </div>
            </div>
          </div>
          <div class="w-[348px] h-[104] px-[24px] flex flex-col gap-[8px]">
            <div class="w-[300px] h-[20px] flex justify-between items-center">
              <div
                class="w-[158px] h-[20px] text-[#667185] text-[14px] DMSans400 flex gap-[4px] items-center"
              >
                <span class="text-[30px] text-[#04802E]">&#8226;</span>
                Charged
              </div>
              <div class="w-[89px] h-[20px]">{{ charged }} members</div>
            </div>
            <div class="w-[300px] h-[20px] flex justify-between items-center">
              <div
                class="w-[163px] h-[20px] text-[#667185] text-[14px] DMSans400 flex gap-[4px] items-center"
              >
                <span class="text-[30px] text-[#E67F4C]">&#8226;</span> About to
                be Burnt Out
              </div>
              <div class="w-[89px] h-[20px]">
                {{ appraochingBurnout }} members
              </div>
            </div>
            <div class="w-[300px] h-[20px] flex justify-between items-center">
              <div
                class="w-[156px] h-[20px] text-[#667185] text-[14px] DMSans400 flex gap-[4px] items-center"
              >
                <span class="text-[30px] text-[#667185]">&#8226;</span>
                Burnout Break
              </div>
              <div class="w-[89px] h-[20px]">{{ onLeave }} members</div>
            </div>
            <div class="w-[300px] h-[20px] flex justify-between items-center">
              <div
                class="w-[156px] h-[20px] text-[#667185] text-[14px] DMSans400 flex gap-[4px] items-center"
              >
                <span class="text-[30px] text-[#D42620]">&#8226;</span> Burnt
                Out
              </div>
              <div class="w-[89px] h-[20px]">{{ burntOut }} members</div>
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
          <div class="w-[232.6px] h-[162.49px] scale-110">
            <ClientOnly>
              <apexchart
                width="100%"
                height="100%"
                type="radialBar"
                :options="chartOptions"
                :series="series"
              />
            </ClientOnly>
          </div>
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
                @click="openModifyBurnoutLimit"
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
          <div class="w-[306px] h-[76px] flex justify-center items-center">
            <div class="w-full bg-gray-200 rounded overflow-hidden">
              <div
                v-if="teamLimit"
                :class="getStatusColor(teamLimit)"
                class="p-1 text-center text-xs font-medium leading-none"
                :style="{ width: `${teamLimit}%` }"
              >
                {{ teamLimit }}%
              </div>
            </div>
          </div>
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
              v-model="searchinput"
              @input="search"
              placeholder="Search by name"
              class="w-[380px] focus:outline-none"
            />
          </div>
          <div class="w-[101px] h-[44px] border rounded-[8px] relative">
            <div
              @click="filterClicked"
              class="w-full h-full flex justify-center items-center"
            >
              Filter
            </div>
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
              @click="selectLead"
              class="border border-[#ACCBEC] rounded-[4px] text-[#2F7DD0] text-[14px] font-medium h-[32px] flex justify-center items-center w-[149px]"
            >
              Change Team Lead
            </div>
          </div>
          <div class="flex gap-[16px] items-center">
            <img
              src="/avatar.png"
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
            class="text-[14px] w-[40px] h-[58px] px-[10px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
          ></th>
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
      </table>
      <div class="overflow-y-scroll h-[930px]">
        <table>
          <tr
            class="border-b text-start"
            v-for="member in filterByName"
            :key="member.full_name"
          >
            <td
              class="text-[14px] w-[40px] h-[58px] px-[10px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
            >
              <div
                @click="openMenuBar(member)"
                class="flex justify-center items-center w-full h-full"
              >
                <img
                  class="w-full h-[20px]"
                  src="/public/menuBar.png"
                  alt="menu-2"
                />
              </div>
            </td>
            <td
              class="text-[14px] w-[281px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
            >
              {{ member.full_name }}
            </td>
            <td
              class="text-[14px] w-[281px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
            >
              <div
                class="flex gap-[8px] h-[21px] w-[76px] rounded-[16px] justify-center items-center text-[#04802E] DMSans500 text-[12px] px-3 bg-[#ECFDF3]"
              >
                <span class="text-[30px] text-[#04802E]">&#8226;</span>
                {{ member.burnout_status }}
              </div>
            </td>
            <td
              class="text-[14px] w-[281px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
            >
              <div
                @click="modifyBurnOutDate(member)"
                class="flex bg-[#F9FAFB] py-[4px] px-[8px] border items-center justify-center gap-[8px] w-[148px] h-[28px]"
              >
                <p class="text-[14px] DMSans500 text-[#667185]">
                  {{ member.last_burnout_date }}
                </p>
                <img src="/assets/icons/PencilSimpleLine.png" alt="" class="" />
              </div>
            </td>
            <td
              class="text-[14px] w-[281px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#667185]"
            >
              {{ member.number_of_done_tasks }}
            </td>
            <td
              class="text-[14px] w-[281px] h-[58px] px-[20px] py-[12px] text-start font-medium DMSans500 text-[#475467]"
            >
              <input
                type="checkbox"
                name=""
                id=""
                class="w-[16px] h-[16px]"
                v-model="member.on_leave"
                @input="assignLeave(member.full_name)"
              />
            </td>
          </tr>
        </table>
      </div>
    </div>
    <!-- <div class="w-[1107px] h-[68px] flex justify-between pt-[12px] pb-[16px]">
      <button
      @click="previousPage"
        class="border rounded-[8px] px-[14px] py-[8px] w-[113px] h-[36px ] text-[14px] font-medium DMSans500 flex gap-[8px] items-center justify-center"
      >
        <div class="pb-[4px]">&larr;</div>
        Previous
      </button>
      <div class="w-[292px] h-[40px] border"></div>
      <button
      @click="nextPage"
        class="border rounded-[8px] px-[14px] py-[8px] w-[113px] h-[36px ] text-[14px] font-medium DMSans500 flex gap-[8px] items-center justify-center"
      >
      
        Next
        <div class="pb-[4px]">&rarr;</div>
      </button>
    </div> -->
  </div>
  <!-- </div> -->

  <div v-if="isModifyBurnoutLimitClicked">
    <ModifyBurnoutLimit
      @closeModal="closeModifyBurnoutLimit"
      :teamId="teamId"
    />
  </div>
  <div v-if="ismodifyBurnOutDateClicked">
    <ModifyLastBurnoutDayModal @close="closeModifyLastBurnoutDayModal" />
  </div>
  <div v-if="isselectLeadClicked">
    <SelectTeamLeadModal
      @close="closeSelectTeamLeadModal"
      :teamMembers="teamMembers"
      :id="teamId"
    />
  </div>
  <div v-if="menuBarClicked">
    <ChangeTeam
      @closeModal="closeChangeTeamModal"
      :memberDetailsToChangeTeam="memberDetailsToChangeTeam"
    />
  </div>
</template>
<script setup>
const toast = useToast();
const baseURL = useRuntimeConfig().public.baseURL;
const searchinput = ref("");
const filterByName = ref([]);
const { id } = useRoute().params;
const IsFilterClicked = ref(false);
const teamMembers = ref([]);
const teamLimit = ref(0);
const teamId = ref("");
if (id === "Design") {
  teamId.value = "9d221e52-952e-48bd-8cb3-ab31fceee060";
} else if (id === "Engineering") {
  teamId.value = "9d221e52-b9ba-4bf1-a94b-f606fda12640";
} else {
  teamId.value = "9d221e52-bf09-4f3d-be39-82bd6fe3d921";
}
// console.log(id, teamId.value);

const filterClicked = () => {
  IsFilterClicked.value = !IsFilterClicked.value;
};
import { useToast } from "vue-toastification";
import ModifyBurnoutLimit from "~/components/ModifyBurnoutLimit.vue";
const isModifyBurnoutLimitClicked = ref(false);
const openModifyBurnoutLimit = () => {
  isModifyBurnoutLimitClicked.value = true;
};
// const page = ref(1);
// const limit = 16;

const closeModifyBurnoutLimit = (value) => {
  isModifyBurnoutLimitClicked.value = value;
};
watchEffect(() => {
  if (id) {
    const { data } = useFetch(`${baseURL}/teams/members/${teamId.value}`);
    teamMembers.value = data.value?.data;

    watchEffect(() => {
      if (searchinput.value === "") {
        return (filterByName.value = teamMembers.value);
      } else {
        // console.log(searchinput.value);
        filterByName.value = teamMembers.value.filter((member) => {
          return member.full_name
            .toLowerCase()
            .includes(searchinput.value.toLowerCase());
        });
      }
    });
  }
});
// const nextPage = () => {
//   page.value++;
// };
// const previousPage = () => {
//   if (page.value > 1) {
//     page.value--;
//   }
// };

const allTeams = ref([]);
const currentTeam = ref([]);
const charged = ref(0);
const appraochingBurnout = ref(0);
const burntOut = ref(0);
const onLeave = ref(0);
const burnOutMeter = ref(0);
const { data: teams } = await useFetch(`${baseURL}/teams/all`);
allTeams.value = teams.value?.data;
const { data: leave } = await useFetch(
  `${baseURL}/teams/members/${teamId.value}?on_leave=true`
);

watchEffect(() => {
  if (leave.value?.data) {
    onLeave.value = leave.value?.data.length;
  }

  if (allTeams.value) {
    currentTeam.value = allTeams.value?.filter((teams) => {
      return teams.id === teamId.value;
    });
    // console.log(currentTeam.value);
    charged.value = currentTeam.value[0].charged;
    appraochingBurnout.value = currentTeam.value[0].about_to_be_burnt_out;
    burntOut.value = currentTeam.value[0].burnt_out;
    teamLimit.value = currentTeam.value[0].burnout_limit.burnout_limit;
    // console.log(teamLimit.value);

    // burnOutMeter.value =
    //   (NO TASK OR CUMMULATIVE BURN OUT POINTS/ teamLimit.value) * 100;
  }
});

const getData = () => {
  return {
    charged: charged.value,
    approaching: appraochingBurnout.value,
    burnt: burntOut.value,
    leave: onLeave.value,
  };
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

const series = ref([0]);
const chartOptions = {
  chart: {
    type: "radialBar",
  },
  labels: ["Meter"],
};
const burntoutMeterStatus = ref("");

watchEffect(() => {
  if (burnOutMeter.value) {
    series.value = burnOutMeter.value;
  }
  if (series.value < 80 || series.value === 80) {
    burntoutMeterStatus.value = "Charged";
  } else if (series.value > 80 || series.value < 95) {
    burntoutMeterStatus.value = "About to be Burnt Out";
  } else if (series.value > 96 || series.value < 100) {
    burntoutMeterStatus.value = "Burnt Out";
  } else {
    burntoutMeterStatus.value = "On a Burnout Break";
  }
});
const allUsers = ref([]);
// onMounted(async () => {
const { data } = await useFetch(`${baseURL}/teams/all`);
allTeams.value = data.value?.data;
const token =
  "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vemVubHkuY2hlY2stZGMuY29tL2F1dGgvc2lnbi1pbiIsImlhdCI6MTc2MzU0NzI5MiwiZXhwIjoxNzk1MDgzMjkyLCJuYmYiOjE3NjM1NDcyOTIsImp0aSI6ImdncEZBN0pSTzRwdVFvbXIiLCJzdWIiOiI5ZDIyMWU1Mi1mM2JjLTRjYjAtYjdhZS04M2MzY2RhYjhkNzUiLCJwcnYiOiIyM2JkNWM4OTQ5ZjYwMGFkYjM5ZTcwMWM0MDA4NzJkYjdhNTk3NmY3In0.ySwKHTErW8TExOu4I8penlupprgvBJGuMOf9WDpcn0w";
const { data: users } = await useFetch(`${baseURL}/users/all`, {
  method: "get",
  headers: {
    Authorization: `Bearer ${token}`,
  },
});
allUsers.value = users.value?.data;
// console.log(allUsers.value);
// });
// const engineering = ref([]);
// const growth = ref([]);
// const design = ref([]);
// const burntOutMeter = ref();
// const Limit = ref();

// const getburnoutMeter = ref("");
// watchEffect(() => {
//   if (!allTeams.value?.length) {
//     engineering.value = allTeams.value?.filter((teams) => {
//       return teams.name === "Engineering";
//     });
//     growth.value = allTeams.value?.filter((teams) => {
//       return teams.name === "Growth";
//     });
//     design.value = allTeams.value?.filter((teams) => {
//       return teams.name === "Design";
//     });
//   }
// });
// watchEffect(() => {
//   if (!allUsers.value?.length && !allTeams.value?.length) {
//     getburnoutMeter.value = allUsers.value?.map((user) => {
//       if (user?.teams[0]?.name === "Design") {
//         Limit.value = design.value[0]?.burnout_limit?.burnout_limit;
//       } else if (user?.teams[0]?.name === "Engineering") {
//         Limit.value = engineering.value[0]?.burnout_limit?.burnout_limit;
//       } else {
//         Limit.value = growth.value[0]?.burnout_limit?.burnout_limit;
//       }
//       user.burnoutMeter = (user.cumulativeBurnoutPoints / Limit.value) * 100;
//     });
//   }
//   console.log(getburnoutMeter.value);
// });
const usersAll = ref([]);
const page1 = ref([]);
const page2 = ref([]);
const getUserId = ref([]);
const theUserId = ref("");

const { data: pg1 } = await useFetch(`${baseURL}/users/all?page=1`, {
  method: "get",
  headers: {
    Authorization: `Bearer ${token} `,
  },
});
page1.value = pg1.value?.data;
const { data: pg2 } = await useFetch(`${baseURL}/users/all?page=2`, {
  method: "get",
  headers: {
    Authorization: `Bearer ${token}`,
  },
});
page2.value = pg2.value?.data;
const userName = ref("");
const assignLeave = (value) => {
  userName.value = value;
  // console.log(value);
};
watchEffect(() => {
  if (page1.value && page2.value) {
    usersAll.value = [...page1.value, ...page2.value];
    // console.log(usersAll.value)

    if (userName.value) {
      getUserId.value = usersAll.value.filter((member) => {
        return member.full_name === userName.value;
      });
      theUserId.value = getUserId.value[0].id;
      // console.log(theUserId.value);
    }
  }
});
watch(theUserId, async (id, oldId) => {
  if (!id || id === oldId) return;

  const { data: toggle } = await useFetch(
    `${baseURL}/users/${id}/toggle-leave`,
    {
      method: "POST",
      headers: {
        Authorization: `Bearer ${token}`,
      },
    }
  );
  // console.log(toggle.value);
  toast.success(`${toggle.value.message}`);
});
const isselectLeadClicked = ref(false);
const selectLead = () => {
  isselectLeadClicked.value = true;
};
const closeSelectTeamLeadModal = (value) => {
  isselectLeadClicked.value = value;
};
const ismodifyBurnOutDateClicked = ref(false);
const modifyBurnOutDate = (value) => {
  ismodifyBurnOutDateClicked.value = true;
  // console.log(value);
};
const menuBarClicked = ref(false);
const memberDetailsToChangeTeam = ref({});
const openMenuBar = (value) => {
  menuBarClicked.value = true;
  memberDetailsToChangeTeam.value = {
    ...value,
    team: id,
    team_id: teamId.value,
  };
};
const closeChangeTeamModal = (value) => {
  menuBarClicked.value = value;
};
const closeModifyLastBurnoutDayModal = (value) => {
  ismodifyBurnOutDateClicked.value = value;
};
</script>
