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
          class="w-[36px] h-[36px] flex justify-center items-center border-[#F0F2F5] border font-bold"
          @click="closeModal"
        >
          x
        </div>
      </div>

      <div
        v-if="data.length !== 0"
        class="overflow-y-scroll overflow-x-hidden flex flex-col gap-[16px] h-[344px] w-[478px]"
      >
        <div v-for="members in data" :key="members.id" class="flex gap-[4px] items-center">
          <img
            src="/assets/css/avatar.png"
            alt=""
            class="w-[46px] h-[46px] rounded-full"
          />
          <div class="h-[49px] flex gap-4 items-center" >
            <p class="text-[16px] text-[#667185] font-semibold DMSans500">
              {{ members?.full_name }}
            </p>

            <div
            :class="getStatusColor(members?.burnout_status)"
              class=" text-[12px] DMSans500 rounded-[16px] h-[25px] px-[8px] py-[2px] flex gap-[4px] items-center"
            >
              <span class="text-[30px]">&#8226;</span>
              {{ members?.burnout_status }}
            </div>
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
  if (status == 'Burnt out') {
    return "bg-red-200 text-[#DC143C]";
  }
  if (status == ' almost Burnt out') {
    return "bg-orange-200 text-[#FA9C1B]";
  }
  return "bg-green-200 text-[#04802E]";
};
</script>
