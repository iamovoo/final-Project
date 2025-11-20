<template>
  <div
    class="fixed bg-[#00000040] top-0 bottom-0 left-0 right-0 flex justify-center items-center"
  >
    <div
      class="border bg-[#FFFFFF] w-[537px] h-[278px] rounded-[12px] flex flex-col"
    >
      <div
        class="w-[537px] h-[166px] pt-[20px] px-[32px] pb-[6px] flex flex-col gap-[24px] justify-center items-center"
      >
        <div class="w-[473px] flex flex-col gap-[4px] h-[86px]">
          <div class="flex justify-between">
            <p
              class="text-[#101928] text-[20px] font-bold flex justify-center items-center"
            >
              Create New Team
            </p>
            <div
              @click="closeModal"
              class="font-bold w-[36px] h-[36px] flex justify-center items-center pb-[5px] border rounded-[4px] border-[#F0F2F5]"
            >
              x
            </div>
          </div>
          <p
            class="text-[#4d5667] font-semibold text-[15px] DMSans500 text-start"
          >
            Enter Team Name (Capitalize if needed)
          </p>
        </div>
        <!-- <div class="w-[473px] h-[56px] px-[32px]"> -->
        <input
          placeholder="Team Name"
          @input="enterTeamName"
          v-model="teamName"
          type="text"
          name=""
          id=""
          class="w-[473px] h-[56px] border-[#E4E7EC] border-2 rounded-[8px] focus:outline-none pl-4"
        />
        <!-- </div> -->
      </div>
      <div class="w-[537px] h-[104px] pt-[28px] px-[32px] pb-[36px]">
        <div class="flex justify-between z-10">
          <button
            @click="closeModal"
            class="text-[16px] bg-[#FFFFFF] text-[#2F7DD0] font-semibold DMSans500 border border-[#ACCBEC] h-[40px] flex justify-center items-center w-[224.5px] z-10"
          >
            Cancel
          </button>
          <button
            @click="saveChanges"
            class="text-[16px] bg-[#2F7DD0] text-[#F9FAFB] font-semibold DMSans500 h-[40px] flex justify-center items-center w-[224.5px] z-10"
          >
            Save Changes
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { useToast } from "vue-toastification";
const userTeamDetails = useCookie("userTeamDetails");
// console.log(userTeamDetails.value)
const baseURL = useRuntimeConfig().public.baseURL;
const toast = useToast();
const teamName = ref("");
const emit = defineEmits(["close"]);
const closeModal = () => {
  emit("close", false);
};
const saveChanges = async () => {
  if (teamName.value) {
    const { data } = await useFetch(`${baseURL}/teams`, {
      method: "POST",
      headers: {
        Authorization: `Bearer ${userTeamDetails.value.access_token}`,
      },
      body: {
        name: `${teamName.value}`,
      },
    });
    toast.success(`${data?.value.data.name} ${data?.value.message}`);
    closeModal();
    teamName.value = "";
  } else {
    toast.error("Kindly enter Team's name");
  }
};
</script>
