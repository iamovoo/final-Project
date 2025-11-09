<template>
  <div class="layout relative">
    <div class="w-[269px] h-[1024px] border-r border-b relative">
      <div class="mt-5 px-[24px] py-[8px]">
        <img src="/assets/css/blue.png" alt="" class="w-[83px] h-[24px]" />
      </div>
      <div
        class="w-[221px] h-[184px] absolute top-[128px] left-[24px] flex flex-col gap-[10px]"
      >
        <div
          class="flex w-[221px] h-[40px] rounded-[8px] items-center gap-[10px] active text-center text-[16px] pl-5"
        >
          <div class="w-[20px] overflow-hidden">
            <img src="/assets/ChartBar.png" alt="" class="object-contain" />
          </div>
          <div class="w-[82px] h-[24px]">
            <p class="DMSans text-center">Dashboard</p>
          </div>
        </div>
        <div
          class="flex w-[221px] h-[40px] rounded-[8px] items-center gap-[10px] text-center text-[16px] pl-5"
        >
          <div class="w-[20px] overflow-hidden">
            <img src="/assets/Users.png" alt="" class="object-contain" />
          </div>
          <div class="w-[49px] h-[24px]">
            <p class="DMSans text-center">Teams</p>
          </div>
        </div>
        <div
          class="flex w-[221px] h-[40px] rounded-[8px] items-center gap-[10px] text-center text-[16px] pl-5"
        >
          <div class="w-[20px] overflow-hidden">
            <img src="/assets/Gear.png" alt="" class="object-contain" />
          </div>
          <div class="w-[63px] h-[24px]">
            <p class="DMSans text-center">Settings</p>
          </div>
        </div>
        <div
          class="flex w-[221px] h-[40px] rounded-[8px] items-center gap-[10px] text-center text-[16px] pl-5"
        >
          <div class="w-[20px] overflow-hidden">
            <img src="/assets/Question.png" alt="" class="object-contain" />
          </div>
          <div class="w-[115px] h-[24px]">
            <p class="DMSans text-center">Help & support</p>
          </div>
        </div>
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
            <img src="/assets/css/logout.png" alt="" class="object-contain" />
          </div>
        </div>
      </div>
    </div>
    <div class="h-[1344px]">
      <div class="w-[1171px] h-[64px] px-[32px] border-b">
        <div class="py-[12px]">
          <div class="w-[1107px] h-[40px] flex justify-between items-center">
            <div
              class="bg-[#F7F9FC] h-[40px] w-[629px] py-[10px] px-[12px] flex items-center gap-[8px]"
            >
              <div class="w-[20px] h-[20px]">
                <img src="/assets/search.png" alt="" class="object-contain" />
              </div>
              <input
                type="search"
                name=""
                id=""
                placeholder="Search here ..."
                class="bg-[#F7F9FC] w-[629px]"
              />
            </div>
            <div
              class="w-[40px] h-[40px] overflow-hidden flex items-center"
              @click="notificationClicked"
            >
              <img
                src="/assets/Notification bell + badge.png"
                alt=""
                class="object-contain"
              />
            </div>
          </div>
        </div>
      </div>
      <div
        class="h-[64px] w-[1171px] py-[16px] px-[32px] flex gap-[20px] border-b items-center"
      >
        <p class="text-[24px] bricolage">Dashboard</p>
        <div
          @click="dateBtnClicked"
          class="py-[4px] px-[8px] w-[88px] h-[28px] rounded-[2px] flex items-center gap-[4px] text-[#F9FAFB] border border-[#E4E7EC]"
        >
          <img
            src="/assets/CalendarBlank.png"
            alt=""
            class="w-[12px] h-[12px]"
          />
          <p class="border-none DMSans500 text-[14px] text-[#667185]">Today</p>
          <img src="/assets/caretDown.png" alt="" class="w-[12px] h-[12px]" />
        </div>

        <div
          class="absolute top-[114px] left-[437px] z-10 shadow-md bg-[#FFFFFF]"
          v-if="isDateClicked"
        >
          <div
            class="w-[240px] h-[200px] border py-[6px] px-[10px] z-10 bg-[#FFFFFF]"
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
      <Notification @closeNotification="closeNotification" />
    </div>
    <div v-if="isSignOutClicked">
      <div
        class="fixed top-0 bottom-0 left-0 right-0 bg-black bg-opacity-50 z-10 flex justify-center items-center"
      >
        <SignoutModal @closeSignoutModal="closeSignoutModal" />
      </div>
    </div>
    <div
      class="absolute top-[160px] left-[301px]"
      @click="isDateClicked = false"
    >
      <slot />
    </div>
  </div>
</template>
<script setup>
import Notification from "~/components/Notification.vue";

const isDateClicked = ref(false);
const isSignOutClicked = ref(false);
const dateBtnClicked = () => {
  isDateClicked.value = !isDateClicked.value;
};
const notificationShow = ref(false);
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
</script>
<style>
.layout {
  display: grid;
  grid-template-columns: 269px 1fr;
}
.active {
  background-color: #d7e6f6;
}
</style>
