<template>
  <div class=" hidden md:block">
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
          </div>
        </div>
      </div>
      <div
        class="w-[600px] h-[648px] border-b-[2px] pb-[36px] flex flex-col gap-[32px]"
      >
        <div class="w-[600px] h-[340px] border-b overflow-y-auto">
          <div v-if="slide === 'All'">
            <div
              class="w-[600px] h-[108px] py-[28px] px-[32px] flex gap-[10px]"
            >
              <div v-if="isSelectClicked">
                <input
                  v-model="isClicked"
                  type="checkbox"
                  name=""
                  id=""
                  class="w-[24px] h-[24px] border border-[#D0D5DD]"
                />
              </div>
              <div class="h-[108px] flex flex-col gap-[8px]">
                <div
                  class="h-[24px] flex justify-between"
                  :class="isSelectClicked ? 'w-[496px]' : 'w-[536px]'"
                >
                  <p class="text-[#2F7DD0] text-[16px] DMSans400 font-bold">
                    New Team Member
                  </p>
                  <p class="text-[#98A2B3] text-[12px] font-medium DMSans500">
                    8:00AM, Oct 21
                  </p>
                </div>
                <div
                  class="h-[24px]"
                  :class="isSelectClicked ? 'w-[496px]' : 'w-[536px]'"
                >
                  <p class="text-[#667185] text-[14px] DMSans400">
                    Jane Doe has accepted an invite to join the Design team.
                  </p>
                </div>
              </div>
            </div>
          </div>
          <div v-if="slide === 'Read'">
            <div
              class="w-[600px] h-[108px] py-[28px] px-[32px] flex gap-[10px]"
            >
              <div v-if="isSelectClicked">
                <input
                  v-model="isClicked"
                  type="checkbox"
                  name=""
                  id=""
                  class="w-[24px] h-[24px] border border-[#D0D5DD]"
                />
              </div>
              <div class="h-[108px] flex flex-col gap-[8px]">
                <div
                  class="h-[24px] flex justify-between"
                  :class="isSelectClicked ? 'w-[496px]' : 'w-[536px]'"
                >
                  <p class="text-[#475367] text-[16px] DMSans400 font-bold">
                    New Team Member
                  </p>
                  <p class="text-[#98A2B3] text-[12px] font-medium DMSans500">
                    8:00AM, Oct 21
                  </p>
                </div>
                <div
                  class="h-[24px]"
                  :class="isSelectClicked ? 'w-[496px]' : 'w-[536px]'"
                >
                  <p class="text-[#667185] text-[14px] DMSans400">
                    Jane Doe has accepted an invite to join the Design team.
                  </p>
                </div>
              </div>
            </div>
          </div>
          <div v-if="slide === 'Unread'">
            <div
              class="w-[600px] h-[108px] py-[28px] px-[32px] flex gap-[10px]"
            >
              <div v-if="isSelectClicked">
                <input
                  v-model="isClicked"
                  type="checkbox"
                  name=""
                  id=""
                  class="w-[24px] h-[24px] border border-[#D0D5DD]"
                />
              </div>
              <div class="h-[108px] flex flex-col gap-[8px]">
                <div
                  class="h-[24px] flex justify-between"
                  :class="isSelectClicked ? 'w-[496px]' : 'w-[536px]'"
                >
                  <p class="text-[#2F7DD0] text-[16px] DMSans400 font-bold">
                    New Team Member
                  </p>
                  <p class="text-[#98A2B3] text-[12px] font-medium DMSans500">
                    8:00AM, Oct 21
                  </p>
                </div>
                <div
                  class="h-[24px]"
                  :class="isSelectClicked ? 'w-[496px]' : 'w-[536px]'"
                >
                  <p class="text-[#667185] text-[14px] DMSans400">
                    Jane Doe has accepted an invite to join the Design team.
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="w-[600px] h-[40px] flex justify-around">
          <div>
            <div
              v-if="isClicked"
              @click="isdeleteNotificationBtnClicked"
              class="w-[256px] h-[40px] border-[#DD524D] flex justify-center items-center text-[#D42620] text-[16px] border font-semibold"
            >
              Delete
            </div>
            <div
              v-if="!isClicked"
              @click="selectBtn"
              class="w-[256px] h-[40px] border-[#ACCBEC] flex justify-center items-center text-[#2F7DD0] text-[16px] border font-semibold"
            >
              {{ selectAndCancel }}
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
        3 notifications deleted successfully
      </div>
    </div>
    <div v-if="isDeleteBtnClicked">
      <DeleteNotificationModal
        @closeModal="cancelCionfirmation"
        @deleteNotification="deleteNotification"
      />
    </div>
  </div>
  <div  class=" block md:hidden">

  </div>
</template>
<script setup>
const isNotificationDeleted = ref(false);
const slide = ref("All");
const isDeleteBtnClicked = ref(false);
const isClicked = ref(false);
watch(isClicked, (newVal, oldVal) => {
  console.log(newVal);
});
const selectAndCancel = ref("Select");
const isSelectClicked = ref(false);
const selectBtn = () => {
  isSelectClicked.value = !isSelectClicked.value;
  if (isSelectClicked.value === true) {
    selectAndCancel.value = "Cancel";
  } else {
    selectAndCancel.value = "Select";
  }
};
const isdeleteNotificationBtnClicked = () => {
  isDeleteBtnClicked.value = true;
};
const cancelCionfirmation = (value) => {
  isDeleteBtnClicked.value = value;
};
const deleteNotification = (value) => {
  isNotificationDeleted.value = value;
  selectBtn();
  isClicked.value = false;
  setTimeout(() => {
    isNotificationDeleted.value = false;
  }, 2000);
};
const showSlide = (value) => {
  slide.value = value;
  isSelectClicked.value = false;
  isClicked.value = false
  selectAndCancel.value = "Select";
  console.log(slide.value);


};
const activeTab = (value) => {
  if (slide.value === value) {
    return "border-b-2 border-[#2F7DD0]";
  }
};
const emit = defineEmits(["closeNotificationExpandModal"]);
const closeModal = () => {
  emit("closeNotificationExpandModal", false);
};
</script>
