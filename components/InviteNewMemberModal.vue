<template>
  <div
    class="fixed bg-[#00000040] top-0 left-0 right-0 bottom-0 flex justify-center items-center"
  >
    <div class="w-[537px] rounded-[12px] bg-white">
      <div class="w-[537px] h-[95px] py-[20px] px-[32px] border-b">
        <div class="w-full h-full flex-col flex justify-between">
          <div class="flex justify-between w-full h-[36px] items-center">
            <p class="text-[#101928] font-medium text-[20px]">
              Invite new members
            </p>
            <div
              @click="cancelModal"
              class="flex justify-center items-center border font-bold w-[36px] h-[36px]"
            >
              x
            </div>
          </div>
          <p class="text-[#667185] font-medium text-[12px] text-start">
            Add new members to your Zenly space
          </p>
        </div>
      </div>
      <div
        class="w-[537px] pt-[28px] px-[32px] pb-[36px] flex flex-col gap-[24px]"
      >
        <div class="h-[84px] w-[473] flex flex-col gap-[12px]">
          <p class="DMSans400 text-[14px]">
            Member’s email<span class="text-[#D42620]">*</span>
          </p>
          <div>
            <input
              v-model="newMemberEmail"
              type="email"
              name=""
              id=""
              class="border w-full p-[14px] border-[#D0D5DD]"
              placeholder="Enter your Member’s Email"
            />
          </div>
        </div>
        <div class="h-[84px] w-[473] flex flex-col gap-[12px]">
          <p class="DMSans400 text-[14px] text-[#98A2B3]">Assign Team</p>
          <div class="w-full flex flex-col gap-[4px]">
            <div class="flex justify-between">
              <p class="DMSans400 text-[14px] text-[#667185]">
                john.doe@company.com
              </p>
              <div
                class="h-[25px] flex items-center py-[4px] px-[8px] border text-[#F9FAFB] border-[#E4E7EC]"
              >
                <p class="DMSans400 text-[14px] text-[#667185]">Design</p>
                <img src="/assets/icons/CaretDown.png" alt="" />
              </div>
            </div>
            <div class="flex justify-between">
              <p class="DMSans400 text-[14px] text-[#667185]">
                john.doe@company.com
              </p>
              <div
                class="h-[25px] flex items-center py-[4px] px-[8px] border text-[#F9FAFB] border-[#E4E7EC]"
              >
                <p class="DMSans400 text-[14px] text-[#667185]">Design</p>
                <img src="/assets/icons/CaretDown.png" alt="" />
              </div>
            </div>
          </div>
        </div>

        <div class="w-[473px] h-[40px]">
          <div class="w-full flex justify-between">
            <button
              @click="cancelModal"
              class="text-[16px] bg-[#FFFFFF] text-[#2F7DD0] font-semibold DMSans500 border border-[#ACCBEC] h-[40px] flex justify-center items-center w-[224.5px] rounded-[4px]"
            >
              Cancel
            </button>
            <button
              @click="sendInvite"
              class="text-[16px] bg-[#2F7DD0] text-[#F9FAFB] font-semibold DMSans500 h-[40px] flex justify-center items-center w-[224.5px] rounded-[4px]"
            >
              Send Invite
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { useToast } from "vue-toastification";

const toast = useToast();
const newMemberEmail = ref("");
const emit = defineEmits(["closeModal"]);
const cancelModal = () => {
  emit("closeModal", false);
};
const sendInvite = () => {
  if (newMemberEmail.value) {
    toast.success("Invites sent successfully");
    cancelModal();
  }
};
</script>
