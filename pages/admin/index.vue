<template>
  <div
    class="h-[64px] w-[1171px] py-[16px] flex gap-[20px] border-b items-center mb-[30px]"
  >
    <p class="text-[24px] bricolage">Dashboard</p>
    <div
      @click="dateBtnClicked"
      class="py-[4px] px-[8px] w-[88px] h-[28px] rounded-[2px] flex items-center gap-[4px] text-[#F9FAFB] border border-[#E4E7EC]"
    >
      <img
        src="/assets/icons/CalendarBlank.png"
        alt=""
        class="w-[12px] h-[12px]"
      />
      <p class="border-none DMSans500 text-[14px] text-[#667185]">Today</p>
      <img src="/assets/icons/CaretDown.png" alt="" class="w-[12px] h-[12px]" />
    </div>

    <div
      class="absolute top-[50px] left-[138px] z-10 shadow-md bg-[#FFFFFF] rounded-[8px]"
      v-if="isDateClicked"
    >
      <div
        class="w-[240px] h-[200px] border py-[6px] px-[10px] z-10 bg-[#FFFFFF] rounded-[8px]"
      >
        <div class="w-[220px] h-[188px] py-[4px]">
          <div class="h-[36px] w-[240px] py-[8px] px-[16px]">
            <p class="text-[14px] DMSans400">Today</p>
          </div>
          <div class="h-[36px] w-[240px] py-[8px] px-[16px]">
            <p class="text-[14px] DMSans400">Last 7 Days</p>
          </div>
          <div class="h-[36px] w-[240px] py-[8px] px-[16px]">
            <p class="text-[14px] DMSans400">Last 30 Days</p>
          </div>
          <div class="h-[36px] w-[240px] py-[8px] px-[16px]">
            <p class="text-[14px] DMSans400">Last 3 Month</p>
          </div>
          <div class="h-[36px] w-[240px] py-[8px] px-[16px]">
            <p class="text-[14px] DMSans400">Last 12 Month</p>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div class="w-[1107px] h-[1241px]">
    <div class="h-[192px] w-[1107px] gap-[20px] flex flex-col">
      <div class="w-[1107px] h-[40px] flex justify-between">
        <p class="text-[20px] font-medium text-[#101928] bricolage">Overview</p>
        <div
          class="w-[205px] h-[40px] text-[16px] flex justify-center items-center font-semibold text-[#F9FAFB] bg-[#2F7DD0] gap-[8px]"
        >
          <img
            src="/assets/icons/UserPlus.png"
            alt=""
            class="w-[16px] h-[16px]"
          />Invite New Member
        </div>
      </div>
      <div class="h-[132px] w-[1107px] gap-[20px] flex">
        <div
          class="w-[258.75px] h-[132px] border p-[24px] rounded-[8px] flex flex-col gap-[24px]"
        >
          <p class="text-[#667185] text-[14px] font-medium">
            Total work members
          </p>
          <div class="w-[210.75px] h-[40px] flex justify-between">
            <p class="font-bold text-[32px] text-[#101928]">51</p>
            <div
              class="w-[40px] h-[40px] overflow-hidden p-[10px] border-[#E4E7EC] rounded-full border"
            >
              <img
                src="/assets/icons/Users.png"
                alt=""
                class="object-contain w-[20px] h-[20px]"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
const userDetails = ref('')
const baseURL = useRuntimeConfig().public.baseURL;
const isDateClicked = ref(false);
const dateBtnClicked = () => {
  isDateClicked.value = !isDateClicked.value;
};
onMounted(async () => {
  userDetails.value = JSON.parse(localStorage.getItem('userDetails'))
  console.log(userDetails.value)
  if(userDetails.value){
  const {data} = await useFetch(`${baseURL}/users/all`,{
    method:'get',
    headers: {
      Authorization: `Bearer ${userDetails.value.access_token}`,
    },
  })
  console.log(data.value)}
})



// const data = await $fetch('https://zenly.check-dc.com/users/all', {
//   headers: {
//     Authorization: `Bearer ${userDetails.access_token}`,
//   },
// })

// console.log(data)

</script>