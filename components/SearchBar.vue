<template>
  <div
    :class="data?.length !== 0 ? 'overflow-y-scroll' : 'overflow-hidden'"
    class="w-[629px] h-[249px] border shadow-sm rounded-[8px]"
  >
    <div v-if="data?.length !== 0">
      <div
        @click="getUserInfo(member)"
        class="w-[629px] h-[41px] flex justify-between px-[16px] py-[8px]"
        v-for="member in data"
        :key="member.full_name"
      >
        <div class="flex gap-[12px]">
          <div class="w-[20px] h-[20px]">
            <img src="/avatar.png" alt="" class="w-[20px] h-[20px]" />
          </div>
          <p class="text-[14px] text-gray-600 font-medium DMSans500">
            {{ member.full_name }}
          </p>
        </div>
        <div class="h-[25px] py-[4px] px-[10px] rounded-[16px]">
          <p
            :class="getTeamColor(member.teams[0]?.name)"
            class="text-[12px] DMSans400 px-5 py-1 rounded-full"
          >
            {{ member.teams[0]?.name }}
          </p>
        </div>
      </div>
    </div>
    <div v-else>
      <div class="w-full h-[240px] flex justify-center items-center">
        <p class="text-gray-500">No result</p>
      </div>
    </div>
  </div>
  <div v-if="isMemberClicked">
    <div
      class="fixed bg-[#00000040] top-0 bottom-0 left-0 right-0 flex justify-center items-center"
    >
      <TeamMemberModal @close="closeTeamMemberDetails" :userDetails="userDetails"/>
    </div>
  </div>
</template>
<script setup>
const baseURL = useRuntimeConfig().public.baseURL;
const isMemberClicked = ref(false);
const prop = defineProps({
  searchData: {
    type: Array,
  },
});
// const data = ref([]);
const data = computed(() => prop.searchData);
console.log(data.value);
const getTeamColor = (value) => {
  if (value === "Design") {
    return "text-[#853C90] bg-[#F6EDF8] ";
  } else if (value === "Engineering") {
    return "bg-blue-200 text-blue-700";
  } else {
    return "bg-green-200 text-green-700";
  }
};
const userDetails = ref({});
const getUserInfo = (member) => {
  userDetails.value = member
  isMemberClicked.value = true;
  // console.log(value);
};
const closeTeamMemberDetails = (value) => {
  isMemberClicked.value = value;
};
</script>
<style></style>
