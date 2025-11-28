<template>
  <div
    class="fixed bg-[#00000040] top-0 bottom-0 right-0 left-0 flex justify-center items-center"
  >
    <div v-if="!showCalender">
      <div class="border bg-[#FFFFFF] w-[537px] h-[250px] rounded-[12px]">
        <div class="w-[537px] h-[146px] pt-[20px] px-[32px] pb-[6px]">
          <div class="w-[473px] flex flex-col gap-[4px] h-[120px]">
            <div class="flex justify-between">
              <p
                class="text-[#101928] text-[20px] font-medium flex justify-center items-center"
              >
                Modify last burnout date
              </p>
              <div
                @click="closeModal"
                class="font-bold w-[36px] h-[36px] flex justify-center items-center pb-[5px] border rounded-[4px] cursor-pointer border-[#F0F2F5]"
              >
                x
              </div>
            </div>
            <div class="w-[473px] h-[84px] flex flex-col justify-between">
              <p
                class="text-[#667185] font-medium text-[14px] DMSans500 text-start"
              >
                Please confirm this information as modifying the Burnout Date
                <br />
                would reset the Burnout Meter to 0%.
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
          <div class="flex justify-between">
            <button
              class="text-[16px] bg-[#FFFFFF] text-[#2F7DD0] font-semibold DMSans500 border border-[#ACCBEC] h-[40px] flex justify-center items-center w-[224.5px]"
            >
              Cancel
            </button>
            <button
              @click="showCalenderBtn"
              class="text-[16px] bg-[#2F7DD0] text-[#F9FAFB] font-semibold DMSans500 h-[40px] flex justify-center items-center w-[224.5px]"
            >
              Yes, I understand
            </button>
          </div>
        </div>
      </div>
    </div>
    <div v-if="showCalender">
      <div class="w-[537px] h-[578px] bg-[#FFFFFF] rounded-[12px] border">
        <div
          class="w-[537px] h-[86px] px-[32px] pt-[20px] pb-[6px] flex flex-col justify-between"
        >
          <div class="flex justify-between">
            <p
              class="text-[#101928] text-[20px] font-medium flex justify-center items-center"
            >
              Modify last burnout date
            </p>
            <div
              @click="closeModal"
              class="font-bold w-[36px] h-[36px] flex justify-center items-center pb-[5px] border rounded-[4px] border-[#F0F2F5]"
            >
              x
            </div>
          </div>
          <p
            class="text-[#667185] font-medium text-[14px] DMSans500 text-start"
          >
            Select last burnout date on the calendar below
          </p>
        </div>
        <div class="w-[537px] h-[388px] px-[32px] pt-[20px] pb-[8px] scale-105">
          <VDatePicker v-model="selectedDate"  style="width: 473px; height: 360px; border-radius: 8px" />
        </div>
        <div class="w-[537px] h-[104px] pt-[28px] px-[32px] pb-[36px]">
          <div class="flex justify-between">
            <button
            @click="closeModal"
              class="text-[16px] bg-[#FFFFFF] text-[#2F7DD0] font-semibold DMSans500 border border-[#ACCBEC] h-[40px] flex justify-center items-center w-[224.5px]"
            >
              Cancel
            </button>
            <button
              @click="showCalenderBtn"
              class="text-[16px] bg-[#2F7DD0] text-[#F9FAFB] font-semibold DMSans500 h-[40px] flex justify-center items-center w-[224.5px]"
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
const showCalender = ref(false);
import { ref } from "vue";
const selectedDate = ref(new Date());
console.log(selectedDate.value);
watch(selectedDate, (newDate, oldValue) => {
  console.log(newDate);
});
const showCalenderBtn = () => {
  showCalender.value = true;
};
const emit = defineEmits(['close'])
const closeModal = ()=>{
emit('close',false)
}
</script>
<style scoped></style>
