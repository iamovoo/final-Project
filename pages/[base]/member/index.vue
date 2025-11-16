<template>
  <div
    class="w-[1107px] h-[64px] py-[16px] border-b border-[#EDEDF0] mb-[49px]"
  >
    <p class="text-[#101928] text-[24px] font-medium bricolage">Dashboard</p>
  </div>
  <div class="w-[1119px] h-[1196px] flex flex-col gap-[80px]">
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
            <p class="text-[#667185] text-[14px] DMSans400">Team</p>
            <div
              :class="
                team === 'Design'
                  ? 'bg-[#F6EDF8] text-[#853C90] '
                  : team === 'Engineering'
                    ? 'bg-blue-200 text-blue-700 '
                    : 'bg-green-200 text-green-700 '
              "
              class="text-[12px] DMSans500 rounded-[16px] h-[25px] px-[10px] py-[4px]"
            >
              {{ team }}
            </div>
          </div>
          <div
            class="w-[352px] h-[32px] flex justify-between items-start border-b"
          >
            <p class="text-[#667185] text-[14px] DMSans400">
              Last Burnout Date
            </p>
            <p class="text-[#1D2739] text-[14px] DMSans400">
              {{ LastBurnOutDate }}
            </p>
          </div>
          <div
            class="w-[352px] h-[32px] flex justify-between items-start border-b"
          >
            <p class="text-[#667185] text-[14px] DMSans400">
              Cumulative Burnout Points
            </p>
            <p class="text-[#1D2739] text-[14px] DMSans400">
              {{ cumulativeBurnoutPoints }}
            </p>
          </div>
          <div
            class="w-[352px] h-[32px] flex justify-between items-start border-b"
          >
            <p class="text-[#667185] text-[14px] DMSans400">Breaks Taken</p>
            <p class="text-[#1D2739] text-[14px] DMSans400">120</p>
          </div>
          <div
            class="w-[352px] h-[32px] flex justify-between items-start border-b"
          >
            <p class="text-[#667185] text-[14px] DMSans400">Tasks Completed</p>
            <p class="text-[#1D2739] text-[14px] DMSans400">4</p>
          </div>
          <div class="w-[352px] h-[25px] flex justify-between items-start">
            <p class="text-[#667185] text-[14px] DMSans400">Leave Status</p>
            <div
              class="bg-[#FEF3CD] text-[#967403] text-[12px] DMSans500 rounded-[16px] h-[25px] px-[10px] py-[4px] flex gap-[4px] items-center"
            >
              <span class="text-[30px] text-[#967403]">&#8226;</span> Due for
              leave
            </div>
          </div>
        </div>
        <div
          class="w-[373px] h-[310px] text-[20px] text-[#101828] flex gap-[16px] rounded-[8px] border p-[20px] justify-center flex-col items-center"
        >
          <div class="h-[73px] w-[333px] flex flex-col justify-between">
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
            <p class="text-[#667185] text-[14px] text-start">
              The percentage of your progress <br />
              toward reaching your burnout limit.
            </p>
          </div>
          <div class="w-[232.59px] h-[162.48806762695312px] border"></div>
        </div>
        <div
          class="w-[310px] h-[310px] text-[20px] text-[#101828] flex flex-col justify-between rounded-[8px] border p-[20px] items-center"
        >
          <div class="w-[270px] h-[92px] flex flex-col justify-between">
            <p class="text-[#1D2739] text-[16px]">Burnout Limit</p>
            <p class="text-[14px] text-[#667185] DMSans400">
              This is the maximum number of points a design team member is
              required to reach to go on a burnout break.
            </p>
          </div>
          <div class="w-[258px] h-[76px]">
            <!-- <apexchart
              width="100%"
              height="100%"
              type="radialBar"
              :options="chartOptions"
              :series="series"
            /> -->
            <div class="w-full bg-gray-200 rounded overflow-hidden">
              <div
                class="bg-green-500 p-2 text-center text-xs font-medium leading-none text-white"
                :style="{ width: teamBurnOutLimit + '%' }"
              >
                {{ teamBurnOutLimit }}%
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="w-[1119px] h-[754px] rounded-[12px] flex flex-col gap-[16px]">
      <div class="h-[100px] w-[1119px] flex flex-col gap-[16px]">
        <div class="flex justify-between">
          <p class="font-medium text-[#101828] text-[20px]">Team members</p>
          <div class="w-[316px] h-[40px] flex justify-end">
            <button
              class="border-[#ACCBEC] text-[#2F7DD0] w-[115px] h-[40px] font-semibold flex items-center justify-center gap-[8px] rounded-[4px] border"
            >
              <img
                src="/assets/icons/ArrowUpRight.png"
                alt=""
                class="h-[16px] w-[16px]"
              />
              View all
            </button>
          </div>
        </div>
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
      <div class="w-[1119px] h-[638px] rounded-[8px]">
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
            v-for="members in teamMembers"
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
    </div>
  </div>
</template>
<script setup>
const baseURL = useRuntimeConfig().public.baseURL;
const userTeamDetails = useCookie("userTeamDetails");
console.log(userTeamDetails.value);
const team = ref(userTeamDetails.value.user.team);
const id = ref(userTeamDetails.value.user.id);
const teamId = ref(null);
const teamMembers = ref("");
const userData = ref("");
const teamBurnOutLimit = ref(null);
onMounted(async () => {
  const { data: user } = await useFetch(`${baseURL}/users/${id.value}`, {
    method: "get",
    headers: {
      Authorization: `Bearer ${userTeamDetails.value.access_token}`,
    },
  });
  userData.value = user.value;
  console.log(user.value);
  teamId.value = user.value?.teams[0]?.id;

  const { data, error } = await useFetch(`${baseURL}/teams/${teamId}`);
  base.value = await data.value;
  teamBurnOutLimit.value = base.value?.burnout_limit.burnout_limit;

  const { data: members } = await useFetch(
    `${baseURL}/teams/members/${teamId}`
  );
  teamMembers.value = await members.value?.data;
});
const LastBurnOutDate = ref("");
const cumulativeBurnoutPoints = ref("");

console.log(teamId);

const base = ref("");

console.log(base.value);

console.log(teamBurnOutLimit.value);

// const series = ref([teamBurnOutLimit]);

// const chartOptions = {
//   chart: {
//     type: "radialBar",
//   },
//   labels: ["Progress"],
// };

console.log(teamMembers.value);
function formatDatePretty(dateString) {
  const date = new Date(dateString);
  const day = date.getDate();
  const lastDigit = String(day).slice(-1);

  let dayWithSuffix;
  if (lastDigit === "1") {
    dayWithSuffix = "st";
  } else if (lastDigit === "2") {
    dayWithSuffix = "nd";
  } else if (lastDigit === "3") {
    dayWithSuffix = "rd";
  } else {
    dayWithSuffix = "th";
  }
  const year = date.getFullYear();
  const month = date.toLocaleString("en-US", { month: "short" });

  return `${day}${dayWithSuffix} ${month}, ${year}`;
}

// const The Burnout Meter = (Cumulative burnout points ÷ Burnout Limit)%
watchEffect(() => {
  if (userData.value) {
    LastBurnOutDate.value = formatDatePretty(
      user.value?.burnout_status[0]?.updated_at
    );
    cumulativeBurnoutPoints.value = user.value?.cumulative_burnout_points;
    console.log(LastBurnOutDate.value, cumulativeBurnoutPoints.value);
  }
});

const IsFilterClicked = ref(false);
const filterClicked = () => {
  IsFilterClicked.value = !IsFilterClicked.value;
};
</script>
