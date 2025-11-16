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
                Modify Burnout Limit
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
                Please confirm you wish to modify the Team Burnout Limit as
                <br />
                this would affect the calculation across every team member’s
                <br />
                Burnout calculation.
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
            @click="editLimitChanges"
              class="text-[16px] bg-[#2F7DD0] text-[#F9FAFB] font-semibold DMSans500 h-[40px] flex justify-center items-center w-[224.5px] z-10"
            >
              Yes, I understand
            </button>
          </div>
        </div>
      </div>
    </div>
    <div v-if="showConfirmationPrompt">
      <div class="border bg-[#FFFFFF] w-[537px] h-[278px] rounded-[12px] flex flex-col">
        <div class="w-[537px] h-[166px] pt-[20px] px-[32px] pb-[6px] flex flex-col gap-[24px] justify-center items-center">
          <div class="w-[473px] flex flex-col gap-[4px] h-[86px]">
            <div class="flex justify-between">
              <p
                class="text-[#101928] text-[20px] font-medium flex justify-center items-center"
              >
                Modify Burnout Limit
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
              Enter a value between 80-100
            </p>
          </div>
          <!-- <div class="w-[473px] h-[56px] px-[32px]"> -->
            <input v-model="burnOutLimitValue" type="number" name="" id="" class="w-[473px] h-[56px] border-[#E4E7EC] border rounded-[8px] focus:outline-none pl-4" />
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
            @click=" saveChanges"
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
import { useToast } from 'vue-toastification';

const toast = useToast()
const burnOutLimitValue= ref('')
const showConfirmationPrompt = ref(false);
const emit = defineEmits(["closeModal"]);
const closeModal = () => {
  emit("closeModal", false);
};
const saveChanges = ()=>{
if(burnOutLimitValue.value){
  toast.success('Burnout Limit Reset')
  burnOutLimitValue.value = ''
  closeModal()
}
}
const editLimitChanges = ()=>{
  showConfirmationPrompt.value = true
}
</script>
