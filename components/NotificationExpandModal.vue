<template>
  <div
    class="fixed top-0 bottom-0 left-0 right-0 bg-[#00000040] z-10 flex justify-center items-center sm:items-center"
  >
    <div
      class="w-[600px] h-[552px] rounded-[12px] border bg-[#FFFFFF] border-[#F0F2F5]"
    >
      <div class="w-[600px] h-[104] pt-[20px] px-[32px]">
        <div class="h-[84px] w-[536px] gap-[8px] flex flex-col">
          <div class="flex justify-between w-[536px] h-[36px]">
            <h6 class="text-[#101928] text-[20px] bricolage font-medium">
              Notifications
            </h6>
            <div
              @click="closeModal"
              class="w-[36px] h-[36px] flex justify-center items-center font-bold"
            >
              x
            </div>
          </div>
          <div class="flex w-[536px] h-[36px] gap-[16px]">
            <div
              @click="showSlide('All')"
              class="w-[40px] h-[40px] flex justify-center"
              :class="activeTab('All')"
            >
              <p class="text-[#98A2B3] text-[16px] bricolage font-semibold">
                All
              </p>
            </div>
            <div
              @click="showSlide('Read')"
              class="w-[59px] h-[40px] flex justify-center"
              :class="activeTab('Read')"
            >
              <p class="text-[#98A2B3] text-[16px] bricolage font-semibold">
                Read
              </p>
            </div>
            <div
              @click="showSlide('Unread')"
              class="w-[76px] h-[40px] flex justify-center"
              :class="activeTab('Unread')"
            >
              <p class="text-[16px] bricolage font-semibold text-[#98A2B3]">
                Unread
              </p>
            </div>
            <div
              v-if="route.includes('admin')"
              @click="showSlide('Sent Invites')"
              class="h-[40px] flex justify-center"
              :class="activeTab('Sent Invites')"
            >
              <p class="text-[#98A2B3] text-[16px] bricolage font-semibold">
                Pending Invites
              </p>
            </div>
          </div>
        </div>
      </div>
      <div
        class="w-[600px] h-[648px] border-b-[2px] pb-[36px] flex flex-col gap-[32px]"
      >
        <div class="w-full h-[340px] border-b overflow-y-auto">
          <div v-if="currentTabTask.length !== 0">
            <div
              v-for="task in currentTabTask"
              class="w-full h-[108px] py-[28px] px-[32px] flex gap-[10px]"
            >
              <div v-if="isSelectClicked">
                <input
                  v-model="isClicked"
                  :value="task"
                  type="checkbox"
                  name="task"
                  id=""
                  class="w-[24px] h-[24px] border border-[#D0D5DD]"
                />
              </div>
              <div class="h-[108px] flex flex-col gap-[8px]">
                <div
                  class="h-[24px] flex justify-between"
                  :class="isSelectClicked ? 'w-[496px]' : 'w-[536px]'"
                >
                  <div v-if="slide === 'Sent Invites'">
                    <p class="text-[#2F7DD0] text-[16px] DMSans400 font-bold">
                      {{ slide }}
                    </p>
                  </div>
                  <div v-else>
                    <p class="text-[#2F7DD0] text-[16px] DMSans400 font-bold">
                      Message
                    </p>
                  </div>
                  <p class="text-[#98A2B3] text-[12px] font-medium DMSans500">
                    {{ task.sent_at }}
                  </p>
                </div>
                <div
                  class="h-[24px]"
                  :class="isSelectClicked ? 'w-[496px]' : 'w-[536px]'"
                >
                  <p class="text-[#667185] text-[14px] DMSans400">
                    {{ task.name }} has accepted an invite to join the Design
                    team.
                  </p>
                </div>
              </div>
            </div>
          </div>
          <div v-else>
            <div class="w-full h-[340px] flex justify-center items-center">
              <p class="text-center text-gray-400">No Message</p>
            </div>
          </div>
        </div>
        <div class="w-[600px] h-[40px] flex justify-around">
          <div>
            <div
              v-if="selectionValue === 'Delete'"
              @click="isdeleteNotificationBtnClicked"
              class="w-[256px] h-[40px] border-[#DD524D] flex justify-center items-center text-[#D42620] text-[16px] border font-semibold"
            >
              Delete
            </div>
            <div
              v-if="selectionValue === 'Select'"
              @click="selectBtn"
              class="w-[256px] h-[40px] border-[#ACCBEC] flex justify-center items-center text-[#2F7DD0] text-[16px] border font-semibold"
            >
              Select
            </div>
            <div
              v-if="selectionValue === 'Cancel'"
              @click="cancelSelect"
              class="w-[256px] h-[40px] border-[#ACCBEC] flex justify-center items-center text-[#2F7DD0] text-[16px] border font-semibold"
            >
              Cancel
            </div>
          </div>
          <button
            class="w-[256px] h-[40px] bg-[#2F7DD0] flex justify-center items-center text-[#F9FAFB] text-[16px] border font-semibold"
          >
            Mark all as read
          </button>
        </div>
      </div>
    </div>

    <div v-if="isNotificationDeleted" class="absolute bottom-[225px]">
      <div
        class="bg-[#1D2739] w-[262px] h-[41px] text-[#FFFFFF] flex justify-center items-center text-[12px]"
      >
        {{ totalDelete }} notifications deleted successfully
      </div>
    </div>
  </div>
  <div v-if="isDeleteBtnClicked">
    <DeleteNotificationModal
      @closeModal="cancelCionfirmation"
      @deleteNotification="deleteNotification"
      :total="isClicked"
    />
  </div>
</template>
<script setup>
const userTeamDetails = useCookie("userTeamDetails", { default: () => {} });
const baseURL = useRuntimeConfig().public.baseURL;
const isNotificationDeleted = ref(false);
const invites = ref([]);
const invitesNotification = ref([]);
const slide = ref("All");
const isDeleteBtnClicked = ref(false);
const pendingInvitesNotification = ref([]);
const isClicked = ref([]);
const totalDelete = ref(null);
const selectionValue = ref("Select");
const isSelectClicked = ref(false);
watch(isClicked, (newVal, oldVal) => {
  if (isClicked.value.length !== 0) {
    selectionValue.value = "Delete";
    totalDelete.value = isClicked.value.length;
  } else if (!isClicked.value.length && isSelectClicked.value === true) {
    selectionValue.value = "Cancel";
  }
  console.log(newVal);
});
const selectBtn = () => {
  selectionValue.value = "Cancel";
  isSelectClicked.value = true;
};
const cancelSelect = () => {
  selectionValue.value = "Select";
  isSelectClicked.value = false;
  if (isClicked.value.length !== 0) {
    isClicked.value = [];
  }
};
const isdeleteNotificationBtnClicked = () => {
  isDeleteBtnClicked.value = true;
};
const cancelCionfirmation = (value) => {
  isDeleteBtnClicked.value = value;
};

const showSlide = (value) => {
  slide.value = value;
  cancelSelect();
};

const activeTab = (value) => {
  if (slide.value === value) {
    return "border-b-2 border-[#2F7DD0]";
  }
};
const currentTabTask = ref([]);
const readTask = ref([]);
const unReadTask = ref([]);
const emit = defineEmits(["closeNotificationExpandModal"]);
const closeModal = () => {
  emit("closeNotificationExpandModal", false);
};
const route = useRoute().path;
if (route.includes("member")) {
  const id = ref("");
  if ((userTeamDetails.value.user.team = "Design")) {
    id.value = "9d221e52-952e-48bd-8cb3-ab31fceee060";
  }
  if ((userTeamDetails.value.user.team = "Engineering")) {
    id.value = "9d221e52-b9ba-4bf1-a94b-f606fda12640";
  } else {
    id.value = "9d221e52-bf09-4f3d-be39-82bd6fe3d921";
  }
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
      currentTabTask.value = [
        {
          title: "Assigned Leave",
          message: "You have been Assigned Leave",
          Date: date,
        },
      ];
    }
  });
} else if (route.includes("admin")) {
  const { data } = await useFetch(`${baseURL}/invites/all`, {
    method: "get",
    headers: {
      Authorization: `Bearer ${userTeamDetails.value.access_token}`,
    },
  });
  invites.value = data.value?.data;
  invites.value = invites.value?.map((m) => ({
    ...m,
    isRead: false,
  }));
  invitesNotification.value = invites?.value?.filter(
    (member) => member.accepted_invite === true
  );
  readTask.value = invitesNotification?.value?.filter(
    (member) => member.isRead === true
  );
  unReadTask.value = invitesNotification?.value?.filter(
    (member) => member.isRead === false
  );
  pendingInvitesNotification.value = invites?.value?.filter(
    (member) => member.accepted_invite === false
  );
  console.log(invitesNotification.value, invites.value);
}
watchEffect(() => {
  if (slide.value === "All") {
    currentTabTask.value = invitesNotification.value;
  } else if (slide.value === "Read") {
    currentTabTask.value = readTask.value;
  } else if (slide.value === "Unread") {
    currentTabTask.value = unReadTask.value;
  } else {
    currentTabTask.value = pendingInvitesNotification.value;
  }
});
const deleteNotification = (value) => {
  isClicked.value.forEach((item) => {
    const i = currentTabTask.value.findIndex((t) => t.id === item.id);
    if (i !== -1) currentTabTask.value.splice(i, 1);
  });
  isClicked.value = [];
  isNotificationDeleted.value = value;
  setTimeout(() => {
    isNotificationDeleted.value = false;
  }, 2000);
};
</script>
