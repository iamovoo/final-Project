<template>
  <div
    class="fixed bg-[#00000040] top-0 bottom-0 right-0 left-0 flex justify-center items-center"
  >
    <div v-if="!showConfirmationPrompt">
      <div class="border bg-[#FFFFFF] w-[537px] h-[278px] rounded-[12px]">
        <div class="w-[537px] h-[174px] pt-[20px] px-[32px] pb-[6px]">
          <div class="w-[473px] flex flex-col gap-[4px] h-[148px]">
            <div class="flex justify-between">
              <p
                class="text-[#101928] text-[20px] font-medium flex justify-center items-center"
              >
                Change Member Team
              </p>
              <div
                @click="closeModal"
                class="font-bold w-[36px] h-[36px] flex justify-center items-center pb-[5px] border rounded-[4px] border-[#F0F2F5]"
              >
                x
              </div>
            </div>
            <div class="w-[473px] h-[112px] flex flex-col justify-between">
              <p
                class="text-[#667185] font-medium text-[14px] DMSans500 text-start"
              >
                Please confirm you wish to Change this Members Team as
                <br />
                this would tranfer him out of his current team
                <br />
              </p>
              <p
                class="text-[#667185] font-medium text-[14px] DMSans500 text-start"
              >
                This action is not reversible.
              </p>
            </div>
          </div>
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
              @click="confirmWarning"
              class="text-[16px] bg-[#2F7DD0] text-[#F9FAFB] font-semibold DMSans500 h-[40px] flex justify-center items-center w-[224.5px] z-10"
            >
              Yes, I understand
            </button>
          </div>
        </div>
      </div>
    </div>
    <div v-if="showConfirmationPrompt">
      <div
        class="border bg-[#FFFFFF] w-[537px] h-[378px] rounded-[12px] flex flex-col"
      >
        <div
          class="w-[537px] pt-[20px] px-[32px] pb-[6px] flex flex-col gap-[24px] justify-center items-center"
        >
          <div class="w-[473px] flex flex-col gap-[4px]">
            <div class="flex justify-between">
              <p
                class="text-[#101928] text-[20px] font-medium flex justify-center items-center"
              >
                Change Member Team
              </p>
              <div
                @click="closeModal"
                class="font-bold w-[36px] h-[36px] flex justify-center items-center pb-[5px] border rounded-[4px] border-[#F0F2F5]"
              >
                x
              </div>
            </div>
          </div>
          <div class="w-full flex flex-col justify-start gap-[4px]">
            <p
              class="text-[#667185] font-medium text-[14px] DMSans500 text-start"
            >
              Name
            </p>
            <input
              disabled
              type="number"
              name=""
              id=""
              :placeholder="`${member?.full_name}`"
              class="w-[473px] h-[56px] border-[#E4E7EC] border-2 rounded-[8px] focus:outline-none pl-4"
            />
          </div>
          <div class="w-full flex flex-col justify-start gap-[4px]">
            <p
              class="text-[#667185] font-medium text-[14px] DMSans500 text-start"
            >
              Enter Team
            </p>
            <input
              @input="watchInput"
              :placeholder="memberTeam"
              v-model="newMemberTeam"
              type="text"
              name=""
              id=""
              class="w-[473px] h-[56px] border-[#E4E7EC] border-2 rounded-[8px] focus:outline-none pl-4"
            />
          </div>
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
  </div>
</template>
<script setup>
import { useToast } from "vue-toastification";
const userTeamDetails = useCookie("userTeamDetails");
// console.log(userTeamDetails.value);
const baseURL = useRuntimeConfig().public.baseURL;
const member = ref();
const memberTeam = ref("");
const newMemberTeam = ref("");
const toast = useToast();
const prop = defineProps({
  memberDetailsToChangeTeam: {
    type: Object,
  },
});
member.value = prop.memberDetailsToChangeTeam;
memberTeam.value = prop.memberDetailsToChangeTeam.team;
console.log(member.value);
const showConfirmationPrompt = ref(false);
const emit = defineEmits(["closeModal"]);
const closeModal = () => {
  emit("closeModal", false);
};

const confirmWarning = () => {
  showConfirmationPrompt.value = true;
};
const usersAll = ref([]);
const page1 = ref([]);
const page2 = ref([]);
const getUserId = ref([]);
const theUserId = ref("");
const getTeambyName = ref([]);
const theTeamId = ref("");
const { data: pg1 } = await useFetch(`${baseURL}/users/all?page=1`, {
  method: "get",
  headers: {
    Authorization: `Bearer ${userTeamDetails.value.access_token} `,
  },
});
page1.value = pg1.value?.data;
const { data: pg2 } = await useFetch(`${baseURL}/users/all?page=2`, {
  method: "get",
  headers: {
    Authorization: `Bearer ${userTeamDetails.value.access_token}`,
  },
});
page2.value = pg2.value?.data;
watchEffect(() => {
  if (page1.value && page2.value) {
    usersAll.value = [...page1.value, ...page2.value];
    console.log(usersAll.value);

    getUserId.value = usersAll.value.filter((m) => {
      return member.value.full_name === m.full_name;
    });
    theUserId.value = getUserId.value[0].id;
    console.log(theUserId.value);
  }
});
// const watchInput = () => {};
const saveChanges = async () => {
  // console.log(theUserId.value, "and", newMemberTeam.value);
  if (theUserId.value !== "" && newMemberTeam.value !== "") {
    getTeambyName.value = usersAll.value.filter((member) => {
      return (
        member?.teams[0]?.name?.toLowerCase() ===
        newMemberTeam.value.toLowerCase()
      );
    });
    theTeamId.value = getTeambyName?.value[0]?.teams[0]?.id;
    // console.log(getTeambyName.value, theTeamId.value);
    if (theTeamId.value !== "") {
      const { data } = await useFetch(
        `${baseURL}/users/${theUserId.value}/change-team`,
        {
          method: "PATCH",
          headers: {
            Authorization: `Bearer ${userTeamDetails.value.access_token}`,
          },
          body: {
            team_id: `${theTeamId.value}`,
          },
        }
      );
      // console.log(data.value);
      toast.success(`${data?.value?.message}`)
    }
  }
  closeModal();
};
</script>
