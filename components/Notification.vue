<template>
  <div class="w-[460px] border flex flex-col">
    <div class="h-[76px] w-[460px] py-[20px] px-[32px]">
      <div class="h-[36px] w-[396px] flex items-center justify-between">
        <div class="h-[28px]">
          <h6 class="text-[20px] font-medium bricolage">Notifications</h6>
        </div>
        <div
          class="h-[36px] w-[36px] border border-[#F0F2F5] font-bold flex justify-center items-center"
          @click="closeNotification"
        >
          x
        </div>
      </div>
    </div>
    <div class="w-[460px] border-b-2 flex flex-col justify-around">
      <div class="w-full overflow-hidden flex flex-col">
        <div v-if="invitesNotification.length !== 0">
          <div
            v-for="task in invitesNotification.slice(-3)"
            class="h-[90px] w-[460px] pb-[30px] px-[32px] flex flex-col gap-[8px]"
          >
            <div v-if="route.includes('member')">
              <div class="w-[396px] h-[24px] flex justify-between items-center">
                <p class="text-[16px] text-[#475367] font-semibold">
                  {{ task.title }}
                </p>
                <p class="text-[12px] text-[#98A2B3] DMSans500">
                  {{ task.Date }}
                </p>
              </div>
              <div
                class="w-[396px] h-[24px] text-[#667185] text-[14px] DMSans400"
              >
                {{ task.message }}
              </div>
            </div>
            <div v-else>
              <div class="w-[396px] h-[24px] flex justify-between items-center">
                <p class="text-[16px] text-[#475367] font-semibold">
                  New Team Member
                </p>
                <p class="text-[12px] text-[#98A2B3] DMSans500">
                  8:00AM, Oct 21
                </p>
              </div>
              <div
                class="w-[396px] h-[24px] text-[#667185] text-[14px] DMSans400"
              >
                {{ task.name }} Ige has joined the Design team.
              </div>
            </div>
          </div>
        </div>
        <div v-else>
          <div class="w-[460px] py-[30px] px-[32px]">
            <p class="text-center text-gray-400">No Message</p>
          </div>
        </div>
      </div>
      <div class="py-[20px]">
        <div class="h-[40px] w-[460px] flex justify-around">
          <button
            class="w-[186px] h-[40px] flex items-center border justify-center text-[#2F7DD0] font-semibold text-[16px] border-[#ACCBEC] rounded-[4px]"
          >
            Mark all as read
          </button>
          <button
            @click="showAllNotifiction"
            class="w-[186px] h-[40px] flex items-center justify-center bg-[#2F7DD0] font-semibold text-[16px] text-white border-[#ACCBEC] rounded-[4px]"
          >
            See all notifications
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
const baseURL = useRuntimeConfig().public.baseURL;
const userTeamDetails = useCookie("userTeamDetails");
console.log(userTeamDetails.value.user);
const invites = ref([]);
const invitesNotification = ref([]);
const emit = defineEmits(["closeNotification", "showAllNotifiction"]);
const closeNotification = () => {
  emit("closeNotification", false);
};
const showAllNotifiction = () => {
  emit("showAllNotifiction", true);
};
const route = useRoute().path;
if (route.includes("admin")) {
  const { data } = await useFetch(`${baseURL}/invites/all`, {
    method: "get",
    headers: {
      Authorization: `Bearer ${userTeamDetails.value.access_token}`,
    },
  });
  invites.value = data.value?.data;
  invitesNotification.value = invites?.value?.filter(
    (member) => member.accepted_invite === true
  );
} else if (route.includes("member")) {
  const id = ref("");
  if ((userTeamDetails.value.user.team === "Design")) {
    id.value = "9d221e52-952e-48bd-8cb3-ab31fceee060";
  }
  if ((userTeamDetails.value.user.team === "Engineering")) {
    id.value = "9d221e52-b9ba-4bf1-a94b-f606fda12640";
  } else {
    id.value = "9d221e52-bf09-4f3d-be39-82bd6fe3d921";
  }
  console.log(id.value)
  const { data } = await useFetch(
    `${baseURL}/teams/members/${id.value}?on_leave=true`,
    {
      method: "get",
      headers: {
        Authorization: `Bearer ${userTeamDetails.value.access_token}`,
      },
    }
  );
  const date = ` ${new Date().getDate()} ${new Date().toLocaleString("en-US", { month: "short" })}, ${new Date().getFullYear()}`;
  console.log(data?.value?.data, date);
  data?.value?.data?.forEach((member) => {
    if (member.full_name === userTeamDetails.value.user.full_name) {
      invitesNotification.value = [
        {
          title: "Assigned Leave",
          message: "You have been Assigned Leave",
          Date: date,
        },
      ];
    } 
  });
}
</script>
