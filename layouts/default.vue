<template>
  <div class="hidden md:block">
    <div class="layout relative">
      <div class="w-[269px] h-[1024px] border-r border-b relative">
        <div class="mt-5 px-[24px] py-[8px]">
          <img src="/assets/icons/blue.png" alt="" class="w-[83px] h-[24px]" />
        </div>
        <div
          class="w-[221px] h-[184px] absolute top-[128px] left-[24px] flex flex-col gap-[10px]"
        >
          <nuxt-link :to="team ? `/${team}/${role}` : `/${role}`">
            <div
              @click="clickedMenu('Dashboard')"
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
              @click="clickedMenu('teams')"
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
              @click="clickedMenu('Settings')"
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
            :to="team ? `/${team}/${role}/HelpAndSupport` : `/${role}/HelpAndSupport`"
          >
            <div
              @click="clickedMenu('Help & support')"
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
        <div class="w-[269px] h-[80px] py-[8px] absolute top-[920px]">
          <div
            class="w-[269px] h-[64px] py-[12px] px-[24px] flex justify-between items-center"
          >
            <div class="w-[184px] h-[40px] flex gap-[12px]">
              <div class="w-[40px] h-[40px]">
                <!-- <div class="bg-[#FFE7CC]"> -->
                <img
                  src="/assets/css/avatar.png"
                  alt=""
                  class="object-contain bg-[#FFE7CC] rounded-[200px]"
                />
                <!-- </div> -->
              </div>
              <div class="w-[132px] h-[40px] flex flex-col">
                <div
                  class="h-[40px] w-[132px] font-semibold text-[14px] DMSans500"
                >
                  Bolaji Folarin
                </div>
                <div
                  class="h-[40px] w-[132px] text-[#475367] text-[14px] DMSans400"
                >
                  Design team lead
                </div>
              </div>
            </div>
            <div class="w-[20px] h-[20px]" @click="signOutClicked">
              <img
                src="/assets/icons/logout.png"
                alt=""
                class="object-contain"
              />
            </div>
          </div>
        </div>
      </div>
      <!-- <div class="h-[1344px]"> -->
      <div class="w-[1171px] h-[64px] px-[32px] border-b">
        <div class="py-[12px]">
          <div class="w-[1107px] h-[40px] flex justify-between items-center">
            <div
              class="bg-[#F7F9FC] h-[40px] w-[629px] py-[10px] px-[12px] flex items-center gap-[8px]"
            >
              <div class="w-[20px] h-[20px]">
                <img
                  src="/assets/icons/search.png"
                  alt=""
                  class="object-contain"
                />
              </div>
              <input
                type="search"
                name=""
                id=""
                placeholder="Search here ..."
                class="bg-[#F7F9FC] w-[629px] border-[#F7F9FC] focus:outline-none"
              />
            </div>
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
          </div>
        </div>
      </div>
      <div
        class="absolute top-[56px] left-[301px] z-10 shadow-sm bg-[#FFFFFF]"
        v-if="false"
      >
        <SearchBar />
      </div>
      <div
        class="absolute top-[60px] left-[948px] z-10 shadow-sm bg-[#FFFFFF]"
        v-if="notificationShow"
      >
        <Notification
          @closeNotification="closeNotification"
          @showAllNotifiction="showAllNotifiction"
        />
      </div>
      <div
        v-if="showAllNotifictionBtnClicked"
        class="fixed top-0 bottom-0 left-0 right-0 bg-[#00000040] z-10 flex justify-center items-center sm:items-center"
      >
        <NotificationExpandModal @closeNotificationExpandModal="closeNotificationExpandModal" />
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
  <div class="block md:hidden">
    <div class="relative">
      <div class="h-[112px] w-[375px] absolute top-[35px]">
        <div class="h-[112px] w-[375px] flex flex-col gap-[8px]">
          <div class="flex justify-between items-center pl-[8px]">
            <div class="px-[24px] py-[8px]">
              <img
                src="/assets/icons/blue.png"
                alt=""
                class="w-[83px] h-[24px]"
              />
            </div>
            <div class="flex h-[40px] w-[88px] justify-between">
              <div
                class="w-[40px] h-[40px] rounded-[20px] bg-[#F0F2F5] flex justify-center items-center"
              >
                <img
                  src="/assets/icons/Notification bell + badge.png"
                  alt=""
                  class="w-[20px] h-[20px]"
                />
              </div>
              <div
                class="w-[40px] h-[40px] rounded-[20px] bg-[#F0F2F5] flex justify-center items-center"
              >
                <img
                  src="/assets/icons/hamburger.png"
                  alt=""
                  class="w-[20px] h-[20px]"
                />
              </div>
            </div>
          </div>
          <div class="h-[64px] w-[375px] py-[12px] px-[20px] bottom-b-1">
            <div
              class="w-[335px] h-[40px] flex bg-[#F7F9FC] justify-center items-center py-[10px] px-[12px] gap-[8px] rounded-[8px] ml-[8px]"
            >
              <img
                src="/assets/icons/search.png"
                alt=""
                class="w-[20px] h-[20px]"
              />
              <input
                type="text"
                name=""
                id=""
                class="w-[335px] bg-[#F7F9FC] rounded-[8px] focus:outline-none"
                placeholder="Search here..."
              />
            </div>
          </div>
        </div>
      </div>
      <div
        class="absolute top-[140px] left-[20px] z-10 shadow-sm bg-[#FFFFFF]"
        v-if="false"
      >
        <SearchBar />
      </div>
      <div
        class="absolute top-[60px] left-[948px] z-10 shadow-sm bg-[#FFFFFF]"
        v-if="notificationShow"
      >
        <Notification @closeNotification="closeNotification" />
      </div>
      <div v-if="isSignOutClicked">
        <div
          class="fixed top-0 bottom-0 left-0 right-0 bg-black bg-opacity-50 z-10 flex justify-center items-end"
        >
          <SignoutModal @closeSignoutModal="closeSignoutModal" />
        </div>
      </div>
      <div
        class="absolute top-[136px] left-[35px]"
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
const showAllNotifictionBtnClicked = ref(false);
const showAllNotifiction = (value) => {
  showAllNotifictionBtnClicked.value = value;
  notificationShow.value = false;
};
const isSignOutClicked = ref(false);
const notificationShow = ref(false);
const closeNotificationExpandModal = (value)=>{
showAllNotifictionBtnClicked.value = value
}
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
console.log(userTeamDetails.value);
const team = ref(userTeamDetails.value.user.team);
const role = ref(userTeamDetails.value.user.role);
console.log(role.value, team.value);
const route = useRoute();

const activeTab = computed(() => {
  if (route.path.includes("/teams")) return "teams";
  if (route.path.includes("/settings")) return "Settings";
  if (route.path.includes("/HelpAndSupport")) return "Help & support";
  else return "Dashboard";
});

// const clickedMenu = (name) => {
//   activeTab.value = name;
//   console.log(name, activeTab.value);
// };
const isActive = (name) => {
  if (name === activeTab.value) return "bg-[#d7e6f6]";
};
</script>
<style>
.layout {
  display: grid;
  grid-template-columns: 269px 1fr;
}
/* .active {
  background-color: #d7e6f6;
} */
</style>
