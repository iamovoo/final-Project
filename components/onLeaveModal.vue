<template>
  <!-- <div class="relative w-[1440px] h-[1024px]"> -->
  <div
    class="fixed top-0 bottom-0 left-0 right-0 bg-black bg-opacity-50 flex justify-center items-center"
  >
    <div
      class="w-[518px] h-[448px] bg-[#FFFFFF] rounded-[8px] p-[20px] flex flex-col gap-[16px] relative"
    >
      <div
        class="w-[478px] h-[48px] pb-[12px] flex justify-between items-center border-b border-[#F0F2F5]"
      >
        <div class="flex items-center h-[28px] gap-[4px] justify-center">
          <h6
            class="text-[#1D2739] text-[20px] flex font-semibold items-center"
          >
            {{ header }}
          </h6>
        </div>
        <div
          class="w-[36px] h-[36px] flex justify-center items-center border-[#F0F2F5] border font-bold cursor-pointer"
          @click="closeModal"
        >
          x
        </div>
      </div>
      <div
        v-if="data.length !== 0"
        class="overflow-y-auto flex flex-col gap-3 h-[344px] w-full pr-2"
      >
        <div
          v-for="member in data"
          :key="member.id"
          class="flex items-center justify-between p-3 rounded-lg border border-gray-200 hover:bg-gray-50 transition"
        >
          <div class="flex items-center gap-3">
            <img src="/avatar.png" class="w-12 h-12 rounded-full" />

            <div class="flex flex-col">
              <p class="text-[16px] text-gray-700 font-semibold">
                {{ member.full_name }}
              </p>
              <p>Member</p>
            </div>
          </div>

          <div
            :class="getStatusColor(member.burnout_status)"
            class="px-3 py-2 rounded-full text-sm font-medium flex gap-[3px] items-center justify-center"
          >
            <span class="text-[30px]">&#8226;</span>
            {{ member.burnout_status }}
          </div>
        </div>
      </div>

      <div v-else class="absolute top-[45%] left-[35%]">
        <p class="text-gray-400 text-[16px]">No {{ title }}</p>
      </div>
    </div>
  </div>
  <!-- </div> -->
</template>

<script setup>
const props = defineProps({
  modalData: {
    type: Array,
  },
  title: {
    type: String,
  },
});
const header = ref(props.title);
const data = ref([]);
data.value = props.modalData;
console.log(header.value);
const emit = defineEmits(["closeModal"]);
const closeModal = () => {
  emit("closeModal", false);
};
const getStatusColor = (status) => {
  if (status == "Burnt out") {
    return "bg-red-200 text-[#DC143C]";
  }
  if (status == " almost Burnt out") {
    return "bg-orange-200 text-[#FA9C1B]";
  }
  return "bg-green-200 text-[#04802E]";
};
</script>
