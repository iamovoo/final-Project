<template>
  <div
    class="w-[533px] h-[510px] py-[20px] px-[24px] rounded-[8px] border flex flex-col gap-[28px] bg-white"
  >
    <div class="h-[28px] w-[485px] flex items-center justify-between">
      <div class="h-[28px]">
        <h6 class="text-[20px] font-medium bricolage">Team Member Details</h6>
      </div>
      <div
        @click="closeModal"
        class="h-[36px] w-[36px] border border-[#F0F2F5] font-bold flex justify-center items-center"
      >
        x
      </div>
    </div>
    <div class="w-[485px] h-[414px] flex flex-col gap-[16px]">
      <div class="w-[485px] h-[32px] flex justify-between items-start border-b">
        <p class="text-[#667185] text-[14px] font-medium DMSans400">Name</p>
        <p class="text-[#101828] text-[14px] font-medium DMSans500">
          {{ member?.full_name }}
        </p>
      </div>
      <div class="w-[485px] h-[32px] flex justify-between items-start border-b">
        <p class="text-[#667185] text-[14px] font-medium DMSans400">Team</p>
        <p
        :class="getTeamColor(member.teams[0]?.name)"
        class=" text-[14px] font-semibold DMSans500 px-2 py-1 rounded-full">
          {{ member.teams[0]?.name }}
        </p>
      </div>
      <div class="w-[485px] h-[32px] flex justify-between items-start border-b">
        <p class="text-[#667185] text-[14px] font-medium DMSans400">
          Last Burnout Date
        </p>
        <p class="text-[#475367] text-[14px] font-medium DMSans500">
          09th Sept, 2024
        </p>
      </div>
      <div class="w-[485px] h-[32px] flex justify-between items-start border-b">
        <p class="text-[#667185] text-[14px] font-medium DMSans400">Email</p>
        <p class="text-[#667185] text-[14px] font-medium DMSans500">
          {{ member?.email }}
        </p>
      </div>
      <div class="w-[485px] h-[32px] flex justify-between items-start border-b">
        <p class="text-[#667185] text-[14px] font-medium DMSans400">
          Cumulative Burnout Points
        </p>
        <p class="text-[#475367] text-[14px] font-medium DMSans500">
          {{ member?.cumulative_burnout_points }}
        </p>
      </div>
      <div class="w-[485px] h-[32px] flex justify-between items-start border-b">
        <p class="text-[#667185] text-[14px] font-medium DMSans400">
          Breaks Taken
        </p>
        <p class="text-[#475367] text-[14px] font-medium DMSans500">
          {{ member?.burnout_breaks?.length }}
        </p>
      </div>
      <div class="w-[485px] h-[32px] flex justify-between items-start border-b">
        <p class="text-[#667185] text-[14px] font-medium DMSans400">
          Burnout Status
        </p>
        <div
          :class="getStatusColor(member?.burnout_status[0]?.name)"
          class="flex gap-[8px] h-[21px] rounded-[16px] justify-center items-center DMSans500 text-[12px] px-3"
        >
          <span class="text-[30px]">&#8226;</span>
          {{ member?.burnout_status[0]?.name }}
        </div>
      </div>
      <div class="w-[485px] h-[32px] flex justify-between items-start border-b">
        <p class="text-[#667185] text-[14px] font-medium DMSans400">
          Tasks Completed
        </p>
        <p class="text-[#101828] text-[14px] font-medium DMSans500">
          {{ member?.monday_tasks?.length }}
        </p>
      </div>
      <div class="w-[485px] h-[32px] flex justify-between items-start border-b">
        <p class="text-[#667185] text-[14px] font-medium DMSans400">
          Leave Status
        </p>
        <div
          :class="getLeaveColor(member.on_leave)"
          class="flex gap-[8px] h-[21px] rounded-[16px] justify-center items-center DMSans500 text-[12px] px-3"
        >
          <span class="text-[30px]">&#8226;</span>
          {{ leaveStatus(member.on_leave) }}
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
const emit = defineEmits(["close"]);
const closeModal = () => {
  emit("close", false);
};
const prop = defineProps({
  userDetails: {
    type: Object,
  },
});
const member = ref({});
member.value = prop.userDetails;
console.log(member.value);
const leaveStatus = (value) => {
  if (value === false) {
    return "Not On Leave";
  } else return "On Leave";
};
const getStatusColor = (value) => {
  if (value == "Burn Out") {
    return "bg-red-200 text-[#DC143C]";
  }
  if (value == "About to be Burnt Out") {
    return "bg-orange-200 text-[#FA9C1B]";
  }
  return " bg-green-200 text-[#04802E]";
};
const getTeamColor = (value) => {
  if (value === "Design") {
    return "text-[#853C90] bg-[#F6EDF8] ";
  } else if (value === "Engineering") {
    return "bg-blue-200 text-blue-700";
  } else {
    return "bg-green-200 text-green-700";
  }
};
const getLeaveColor = (value) => {
  if (value == false) {
    return "bg-green-200 text-[#04802E]";
  } else {
    return "bg-gray-200 text-gray-700";
  }
};
</script>
