<template>
  <div class="hidden md:block">
    <div class="layout relative">
      <div
        class="w-[269px] h-[1024px] border-r border-b fixed"
        @click="isSearchInput = false"
      >
        <div class="mt-5 px-[24px] py-[8px]">
          <img src="/assets/icons/blue.png" alt="" class="w-[83px] h-[24px]" />
        </div>
        <div
          class="w-[221px] h-[184px] absolute top-[128px] left-[24px] flex flex-col gap-[10px]"
        >
          <nuxt-link :to="team ? `/${team}/${role}` : `/${role}`">
            <div
              :class="isActive('Dashboard')"
              class="flex w-[221px] h-[40px] rounded-[8px] items-center gap-[10px] text-center text-[16px] pl-5"
            >
              <div class="w-[20px] overflow-hidden">
                <img
                  src="/assets/icons/ChartBar.png"
                  alt=""
                  class="object-contain"
                />
              </div>
              <div class="w-[82px] h-[24px]">
                <p class="DMSans text-center">Dashboard</p>
              </div>
            </div>
          </nuxt-link>
          <nuxt-link :to="team ? `/${team}/${role}/teams` : `/${role}/teams`">
            <div
              :class="isActive('teams')"
              class="flex w-[221px] h-[40px] rounded-[8px] items-center gap-[10px] text-center text-[16px] pl-5"
            >
              <div class="w-[20px] overflow-hidden">
                <img
                  src="/assets/icons/Users.png"
                  alt=""
                  class="object-contain"
                />
              </div>
              <div class="w-[49px] h-[24px]">
                <p class="DMSans text-center">Teams</p>
              </div>
            </div>
          </nuxt-link>
          <nuxt-link
            :to="team ? `/${team}/${role}/settings` : `/${role}/settings`"
          >
            <div
              :class="isActive('Settings')"
              class="flex w-[221px] h-[40px] rounded-[8px] items-center gap-[10px] text-center text-[16px] pl-5"
            >
              <div class="w-[20px] overflow-hidden">
                <img
                  src="/assets/icons/Gear.png"
                  alt=""
                  class="object-contain"
                />
              </div>
              <div class="w-[63px] h-[24px]">
                <p class="DMSans text-center">Settings</p>
              </div>
            </div>
          </nuxt-link>
          <nuxt-link
            :to="
              team
                ? `/${team}/${role}/HelpAndSupport`
                : `/${role}/HelpAndSupport`
            "
          >
            <div
              :class="isActive('Help & support')"
              class="flex w-[221px] h-[40px] rounded-[8px] items-center gap-[10px] text-center text-[16px] pl-5"
            >
              <div class="w-[20px] overflow-hidden">
                <img
                  src="/assets/icons/Question.png"
                  alt=""
                  class="object-contain"
                />
              </div>
              <div class="w-[115px] h-[24px]">
                <p class="DMSans text-center">Help & support</p>
              </div>
            </div>
          </nuxt-link>
        </div>
        <div class="w-[269px] h-[80px] py-[8px] absolute top-[600px]">
          <div
            class="w-[269px] h-[64px] py-[12px] px-[24px] flex justify-between items-center"
          >
            <div class="w-[184px] h-[40px] flex gap-[12px]">
              <img
                src="/avatar.png"
                alt=""
                width="40"
                height="40"
                class="w-[40px] h-[40px] bg-[#FFE7CC] rounded-full object-contain"
              />

              <div class="w-[132px] h-[40px] flex flex-col">
                <div
                  class="h-[40px] w-[132px] font-semibold text-[14px] DMSans500"
                >
                  {{ fullname }}
                </div>
                <div
                  class="h-[40px] w-[132px] text-[#475367] text-[14px] DMSans400"
                >
                  {{ role }}
                </div>
              </div>
            </div>
            <div class="w-[20px] h-[20px]" @click="signOutClicked">
              <img
                src="/assets/icons/logout.png"
                alt=""
                width="20"
                height="20"
                class="w-[20px] h-[20px] object-contain"
              />
            </div>
          </div>
        </div>
      </div>
      <!-- <div class="h-[1344px]"> -->
      <div
        class="w-[1171px] h-[64px] px-[32px] border-b fixed left-[270px] z-10 bg-white"
      >
        <div class="py-[12px]">
          <div class="w-[1107px] h-[40px] flex justify-between items-center">
            <div
              class="bg-[#F7F9FC] h-[40px] w-[629px] py-[10px] px-[12px] flex items-center gap-[8px]"
            >
              <div class="w-[20px] h-[20px]">
                <img
                  src="/assets/icons/search.png"
                  alt=""
                  class="w-[20px] h-[20px]"
                />
              </div>
              <input
                v-model="globalSearch"
                @input="searchBy"
                type="text"
                name=""
                id=""
                placeholder="Search here ..."
                class="bg-[#F7F9FC] w-[629px] border-[#F7F9FC] focus:outline-none"
              />
            </div>
            <div class="relative">
              <div
                class="w-[40px] h-[40px] overflow-hidden flex items-center justify-center bg-[#F0F2F5] rounded-[20px]"
                @click="notificationClicked"
              >
                <img
                  src="/assets/icons/Notification bell + badge.png"
                  alt=""
                  class="object-contain"
                />
              </div>

              <div
                class="absolute bottom-[-15px] right-0 translate-y-full z-10 shadow-sm bg-[#FFFFFF]"
                v-if="notificationShow"
              >
                <Notification
                  @closeNotification="closeNotification"
                  @showAllNotifiction="showAllNotifiction"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
      <div
        class="absolute top-[56px] left-[301px] z-10 shadow-sm bg-[#FFFFFF]"
        v-if="isSearchInput"
      >
        <SearchBar :searchData="filtered" />
      </div>

      <div v-if="showAllNotifictionBtnClicked">
        <NotificationExpandModal
          @closeNotificationExpandModal="closeNotificationExpandModal"
        />
      </div>
      <div v-if="isSignOutClicked">
        <div
          class="fixed top-0 bottom-0 left-0 right-0 bg-[#00000040] z-10 flex justify-center items-center"
        >
          <SignoutModal @closeSignoutModal="closeSignoutModal" />
        </div>
      </div>
      <div
        class="absolute top-[65px] left-[301px]"
        @click="isDateClicked = false"
      >
        <slot />
      </div>
    </div>
  </div>
</template>
<script setup>
import Notification from "~/components/Notification.vue";
import NotificationExpandModal from "~/components/NotificationExpandModal.vue";
const baseURL = useRuntimeConfig().public.baseURL;
const showAllNotifictionBtnClicked = ref(false);
const showAllNotifiction = (value) => {
  showAllNotifictionBtnClicked.value = value;
  notificationShow.value = false;
};
const isSignOutClicked = ref(false);
const notificationShow = ref(false);
const closeNotificationExpandModal = (value) => {
  showAllNotifictionBtnClicked.value = value;
};
const notificationClicked = () => {
  notificationShow.value = true;
};
const closeNotification = (value) => {
  notificationShow.value = value;
};
const closeSignoutModal = (value) => {
  isSignOutClicked.value = value;
};
const signOutClicked = () => {
  isSignOutClicked.value = true;
};
const userTeamDetails = useCookie("userTeamDetails");
// console.log(userTeamDetails.value);
const team = ref(userTeamDetails.value.user.team);
const role = ref(userTeamDetails.value.user.role);
const fullname = ref(userTeamDetails.value.user.full_name);
// console.log(role.value, team.value);
const route = useRoute();

const activeTab = computed(() => {
  if (route.path.includes("/teams")) return "teams";
  if (route.path.includes("/settings")) return "Settings";
  if (route.path.includes("/HelpAndSupport")) return "Help & support";
  else return "Dashboard";
});
const allUsers = ref([]);
const isActive = (name) => {
  if (name === activeTab.value) return "bg-[#d7e6f6]";
};
const globalSearch = ref("");
const isSearchInput = ref(false);
const filtered = ref([]);
const searchBy = async () => {
  if (globalSearch.value) {
    isSearchInput.value = true;
    const { data: page1 } = await useFetch(`${baseURL}/users/all?page=1`, {
      method: "get",
      headers: {
        Authorization: `Bearer ${userTeamDetails.value.access_token}`,
      },
    });
    const { data: page2 } = await useFetch(`${baseURL}/users/all?page=2`, {
      method: "get",
      headers: {
        Authorization: `Bearer ${userTeamDetails.value.access_token}`,
      },
    });
    allUsers.value = [
      ...(page1.value?.data || []),
      ...(page2.value?.data || []),
    ];
    filtered.value = allUsers.value.filter((member) => {
      return member.full_name
        .toLowerCase()
        .includes(globalSearch.value.toLowerCase());
    });
    // console.log(globalSearch.value, filtered.value);
  } else {
    isSearchInput.value = false;
  }
};
</script>
<style>
.layout {
  display: grid;
  grid-template-columns: 269px 1fr;
}
</style>
