<template>
 
    <!-- <div class="relative w-[1440px] h-[1024px]"> -->
    <div
      class="fixed top-0 bottom-0 left-0 right-0 bg-black bg-opacity-50 flex justify-center items-center z-10"
    >
      <div
        class="w-[518px] h-[448px] bg-[#FFFFFF] rounded-[8px] p-[20px] flex flex-col gap-[16px]"
      >
        <div
          class="w-[478px] h-[48px] pb-[12px] flex justify-between items-center border-b border-[#F0F2F5]"
        >
          <div class="flex items-center h-[28px] gap-[4px] justify-center">
            <h6
              class="text-[#1D2739] text-[20px] flex font-semibold items-center"
            >
              Members nearing burnout
            </h6>
            <div
              class="w-[23px] h-[25px] bg-[#FCEFE9] rounded-[16px] text-[#B34C19] text-[12px] p-[4px]"
            >
              20
            </div>
          </div>
          <div
            class="w-[36px] h-[36px] flex justify-center items-center border-[#F0F2F5] border cursor-pointer"
            @click="closeModal"
          >
            x
          </div>
        </div>

        <div
          class="overflow-y-scroll overflow-x-hidden flex flex-col gap-[16px] h-[344px] w-[478px]"
        >
          <div
            class="w-full h-[44px] flex justify-between items-center border-b border-[#F0F2F5] mb-[10px]"
          >
            <p class="text-[#667185] text-[14px] DMSans400">
              Oluwaseun Adebayo
            </p>
            <div
              class="h-[32px] w-[288px] flex justify-between items-center pr-3"
            >
              <div
                class="text-[#B34C19] text-[12px] bg-[#FCEFE9] py-[2px] pl-[6px] pr-[8px]"
              >
                Almost Burnt Out
              </div>
              <button
                class="flex gap-[6px] items-center justify-center text-[#2F7DD0] text-[14px] border border-[#ACCBEC]"
              >
                <img
                  src="/assets/icons/ArrowUpRight.png"
                  alt=""
                  class="w-[14px] h-[14px]"
                />
                Assign leave
              </button>
            </div>
          </div>
          <div
            class="w-full h-[44px] flex justify-between items-center border-b border-[#F0F2F5] mb-[10px]"
          >
            <p class="text-[#667185] text-[14px] DMSans400">
              Oluwaseun Adebayo
            </p>
            <div
              class="h-[32px] w-[288px] flex justify-between items-center pr-3"
            >
              <div
                class="text-[#B34C19] text-[12px] bg-[#FCEFE9] py-[2px] pl-[6px] pr-[8px]"
              >
                Almost Burnt Out
              </div>
              <button
                class="flex gap-[6px] items-center justify-center text-[#2F7DD0] text-[14px] border border-[#ACCBEC]"
              >
                <img
                  src="/assets/icons/ArrowUpRight.png"
                  alt=""
                  class="w-[14px] h-[14px]"
                />
                Assign leave
              </button>
            </div>
          </div>
          <div
            class="w-full h-[44px] flex justify-between items-center border-b border-[#F0F2F5] mb-[10px]"
          >
            <p class="text-[#667185] text-[14px] DMSans400">
              Oluwaseun Adebayo
            </p>
            <div
              class="h-[32px] w-[288px] flex justify-between items-center pr-3"
            >
              <div
                class="text-[#B34C19] text-[12px] bg-[#FCEFE9] py-[2px] pl-[6px] pr-[8px]"
              >
                Almost Burnt Out
              </div>
              <button
                class="flex gap-[6px] items-center justify-center text-[#2F7DD0] text-[14px] border border-[#ACCBEC]"
              >
                <img
                  src="/assets/icons/ArrowUpRight.png"
                  alt=""
                  class="w-[14px] h-[14px]"
                />
                Assign leave
              </button>
            </div>
          </div>
          <div
            class="w-full h-[44px] flex justify-between items-center border-b border-[#F0F2F5] mb-[10px]"
          >
            <p class="text-[#667185] text-[14px] DMSans400">
              Oluwaseun Adebayo
            </p>
            <div
              class="h-[32px] w-[288px] flex justify-between items-center pr-3"
            >
              <div
                class="text-[#B34C19] text-[12px] bg-[#FCEFE9] py-[2px] pl-[6px] pr-[8px]"
              >
                Almost Burnt Out
              </div>
              <button
                class="flex gap-[6px] items-center justify-center text-[#2F7DD0] text-[14px] border border-[#ACCBEC]"
              >
                <img
                  src="/assets/icons/ArrowUpRight.png"
                  alt=""
                  class="w-[14px] h-[14px]"
                />
                Assign leave
              </button>
            </div>
          </div>
          <div
            class="w-full h-[44px] flex justify-between items-center border-b border-[#F0F2F5] mb-[10px]"
          >
            <p class="text-[#667185] text-[14px] DMSans400">
              Oluwaseun Adebayo
            </p>
            <div
              class="h-[32px] w-[288px] flex justify-between items-center pr-3"
            >
              <div
                class="text-[#B34C19] text-[12px] bg-[#FCEFE9] py-[2px] pl-[6px] pr-[8px]"
              >
                Almost Burnt Out
              </div>
              <button
                class="flex gap-[6px] items-center justify-center text-[#2F7DD0] text-[14px] border border-[#ACCBEC]"
              >
                <img
                  src="/assets/icons/ArrowUpRight.png"
                  alt=""
                  class="w-[14px] h-[14px]"
                />
                Assign leave
              </button>
            </div>
          </div>
          <div
            class="w-full h-[44px] flex justify-between items-center border-b border-[#F0F2F5] mb-[10px]"
          >
            <p class="text-[#667185] text-[14px] DMSans400">
              Oluwaseun Adebayo
            </p>
            <div
              class="h-[32px] w-[288px] flex justify-between items-center pr-3"
            >
              <div
                class="text-[#B34C19] text-[12px] bg-[#FCEFE9] py-[2px] pl-[6px] pr-[8px]"
              >
                Almost Burnt Out
              </div>
              <button
                class="flex gap-[6px] items-center justify-center text-[#2F7DD0] text-[14px] border border-[#ACCBEC]"
              >
                <img
                  src="/assets/icons/ArrowUpRight.png"
                  alt=""
                  class="w-[14px] h-[14px]"
                />
                Assign leave
              </button>
            </div>
          </div>
          <div
            class="w-full h-[44px] flex justify-between items-center border-b border-[#F0F2F5] mb-[10px]"
          >
            <p class="text-[#667185] text-[14px] DMSans400">
              Oluwaseun Adebayo
            </p>
            <div
              class="h-[32px] w-[288px] flex justify-between items-center pr-3"
            >
              <div
                class="text-[#B34C19] text-[12px] bg-[#FCEFE9] py-[2px] pl-[6px] pr-[8px]"
              >
                Almost Burnt Out
              </div>
              <button
                class="flex gap-[6px] items-center justify-center text-[#2F7DD0] text-[14px] border border-[#ACCBEC]"
              >
                <img
                  src="/assets/icons/ArrowUpRight.png"
                  alt=""
                  class="w-[14px] h-[14px]"
                />
                Assign leave
              </button>
            </div>
          </div>
          <div
            class="w-full h-[44px] flex justify-between items-center border-b border-[#F0F2F5] mb-[10px]"
          >
            <p class="text-[#667185] text-[14px] DMSans400">
              Oluwaseun Adebayo
            </p>
            <div
              class="h-[32px] w-[288px] flex justify-between items-center pr-3"
            >
              <div
                class="text-[#B34C19] text-[12px] bg-[#FCEFE9] py-[2px] pl-[6px] pr-[8px]"
              >
                Almost Burnt Out
              </div>
              <button
                class="flex gap-[6px] items-center justify-center text-[#2F7DD0] text-[14px] border border-[#ACCBEC]"
              >
                <img
                  src="/assets/icons/ArrowUpRight.png"
                  alt=""
                  class="w-[14px] h-[14px]"
                />
                Assign leave
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- </div> -->
</template>

<script setup>
const emit = defineEmits(["closeModal"]);
const closeModal = () => {
  emit("closeModal", false);
};
</script>
