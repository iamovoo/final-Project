<template>
  <div
    class="fixed bg-[#00000040] top-0 bottom-0 left-0 right-0 flex justify-center items-center"
  >
    <div class="bg-white h-[672px] w-[537px] border">
      <div
        class="flex justify-between border-b-2 border pt-[20px] px-[32px] pb-[16px]"
      >
        <h4 class="text-[20px] text-[#101928] font-medium">Select Team Lead</h4>
        <div @click="closeModal" class="font-bold text-[20px]">x</div>
      </div>
      <div
        class="h-[600px] w-full pt-[24px] pb-[28px] px-[32px] flex flex-col gap-[16px]"
      >
        <div class="flex flex-col justify-between h-[76px] w-full">
          <p class="font-semibold text-[16px] text-[#667185]">Team Member</p>
          <input
            v-model="searchInput"
            type="text"
            name=""
            id=""
            placeholder="Search"
            class="h-[44px] w-full border-2 rounded-md p-2 focus:outline-none"
          />
        </div>
        <div class="w-full h-[384px] overflow-y-auto flex flex-col gap-[16px]">
          <div
            class="flex justify-between items-center w-full h-[24px] pr-3"
            v-for="member in filteredMembers"
          >
            <p class="text-[16px] text-[#667185] font-semibold">
              {{ member.full_name }}
            </p>
            <input
              @click="getData(member.full_name)"
              type="radio"
              name="teamLead"
              :id="`${member.full_name}`"
              class="w-[24px] h-[24px] border-gray-200"
            />
          </div>
        </div>
        <div class="h-[40px] w-full flex justify-between">
          <div
            @click="closeModal"
            class="w-[224.5px] h-full flex justify-center items-center border border-[#ACCBEC]"
          >
            <p class="font-semibold text-[16px] text-[#2F7DD0]">Cancel</p>
          </div>
          <div
          @click="save"
            class="w-[224.5px] h-full flex justify-center items-center bg-[#2F7DD0]"
          >
            <p class="font-semibold text-[16px] text-[#F9FAFB]">Save Changes</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
const baseURL = useRuntimeConfig().public.baseURL;
const userTeamDetails = useCookie("userTeamDetails", { default: () => {} });
// console.log(userTeamDetails.value)
const emit = defineEmits(["close"]);
const closeModal = () => {
  emit("close", false);
};
const props = defineProps({
  teamMembers: {
    type: Array,
  },
  id: {
    type: String,
  },
});
const members = ref([]);
const id = ref("");
members.value = props.teamMembers;
id.value = props.id;
// console.log(members.value, id.value);

const searchInput = ref();
const filteredMembers = ref([]);
watchEffect(() => {
  if (!searchInput.value) {
    filteredMembers.value = members.value;
  } else {
    filteredMembers.value = members.value?.filter((member) => {
      return member.full_name
        .toLowerCase()
        .includes(searchInput.value.toLowerCase());
    });
  }
  // console.log(searchInput.value, filteredMembers.value);
});
const allUsers = ref([]);
const Selected = ref("");
const TeamLeadEmail = ref("");
const selectedTeamLead = ref([]);
const getData = async (value) => {
  Selected.value = value;
  // console.log(Selected.value);

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
  allUsers.value = [...(page1.value?.data || []), ...(page2.value?.data || [])];
  selectedTeamLead.value = allUsers.value.filter((member) => {
    return member.full_name.includes(Selected.value);
  });
  TeamLeadEmail.value = selectedTeamLead.value[0]?.email;
  // console.log(selectedTeamLead.value, TeamLeadEmail.value);
};
const save = async ()=>{
  if (TeamLeadEmail.value !== "") {
    const { data } = await useFetch(`${baseURL}/invites`, {
      method: "POST",
      headers: {
        Authorization: `Bearer ${userTeamDetails.value.access_token}`,
      },
      body: {
        team_id: `${id.value}`,
        name: `${Selected.value}`,
        email: `${TeamLeadEmail.value}`,
      },
    });
    // console.log(data.value, id.value, Selected.value, TeamLeadEmail.value);
  }
  closeModal()
}
</script>
