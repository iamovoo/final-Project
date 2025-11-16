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

  <div class="w-[1107px] h-[1241px] flex flex-col gap-[36px]">
    <div class="h-[192px] w-[1107px] gap-[20px] flex flex-col">
      <div class="w-[1107px] h-[40px] flex justify-between">
        <p class="text-[20px] font-medium text-[#101928] bricolage">Overview</p>
        <div
          @click="inviteMembers"
          class="w-[205px] h-[40px] text-[16px] flex justify-center items-center font-semibold text-[#F9FAFB] bg-[#2F7DD0] gap-[8px] rounded-[4px]"
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
            <p class="font-bold text-[32px] text-[#101928]">{{totalMembers}}</p>
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
        <div
          class="w-[258.75px] h-[132px] border p-[24px] rounded-[8px] flex flex-col gap-[24px]"
        >
          <p class="text-[#667185] text-[14px] font-medium">Members on Leave</p>
          <div class="w-[210.75px] h-[40px] flex justify-between">
            <p class="font-bold text-[32px] text-[#101928]">40</p>
            <div
              class="w-[40px] h-[40px] overflow-hidden p-[10px] border-[#E4E7EC] rounded-full border"
            >
              <img
                src="/assets/icons/blueUsers.png"
                alt=""
                class="object-contain w-[20px] h-[20px]"
              />
            </div>
          </div>
        </div>
        <div
          class="w-[258.75px] h-[132px] border p-[24px] rounded-[8px] flex flex-col gap-[24px]"
        >
          <p class="text-[#667185] text-[14px] font-medium">
            Appraoching Burnout
          </p>
          <div class="w-[210.75px] h-[40px] flex justify-between">
            <p class="font-bold text-[32px] text-[#101928]">15</p>
            <div
              class="w-[40px] h-[40px] overflow-hidden p-[10px] border-[#E4E7EC] rounded-full border"
            >
              <img
                src="/assets/icons/orangeUsers.png"
                alt=""
                class="object-contain w-[20px] h-[20px]"
              />
            </div>
          </div>
        </div>
        <div
          class="w-[258.75px] h-[132px] border p-[24px] rounded-[8px] flex flex-col gap-[24px]"
        >
          <p class="text-[#667185] text-[14px] font-medium">Burnt Out</p>
          <div class="w-[210.75px] h-[40px] flex justify-between">
            <p class="font-bold text-[32px] text-[#101928]">10</p>
            <div
              class="w-[40px] h-[40px] overflow-hidden p-[10px] border-[#E4E7EC] rounded-full border"
            >
              <img
                src="/assets/icons/redUsers.png"
                alt=""
                class="object-contain w-[20px] h-[20px]"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="w-[1107px] h-[566px] flex flex-col gap-[36px]">
      <div class="w-[1107px] h-[152px] flex gap-[24px]">
        <div
          class="w-[502px] h-[152px] flex flex-col justify-between pt-[20px] px-[30px] pb-[26px] bg-[#2F7DD0] rounded-[8px]"
        >
          <p class="font-semibold text-[18px] text-[#667185] DMSans500">
            Average Burnout Percentage
          </p>
          <p class="font-bold text-[32px] text-[#F9FAFB] DMSans500">62%</p>
          <div class="w-[442px] h-[5px] rounded-[4px] bg-[#F9FAFB]"></div>
        </div>
        <div
          class="w-[581px] h-[152px] flex border justify-between pt-[20px] px-[30px] pb-[26px] rounded-[8px]"
        >
          <div
            class="w-[154.3333282470703px] h-[106px] flex flex-col justify-between rounded-[8px]"
          >
            <p class="font-medium text-[14px] text-[#667185] DMSans500">
              Design
            </p>
            <p class="font-bold text-[32px] text-[#FA9C1B] DMSans500">62%</p>
            <div class="w-[154px] h-[5px] rounded-[4px] bg-[#FA9C1B]"></div>
          </div>
          <div
            class="w-[154.3333282470703px] h-[106px] flex flex-col justify-between rounded-[8px]"
          >
            <p class="font-semibold text-[14px] text-[#667185] DMSans500">
              Engineering
            </p>
            <p class="font-bold text-[32px] text-[#FA9C1B] DMSans500">22%</p>
            <div class="w-[154px] h-[5px] rounded-[4px] bg-[#FA9C1B]"></div>
          </div>
          <div
            class="w-[154.3333282470703px] h-[106px] flex flex-col justify-between rounded-[8px]"
          >
            <p class="font-semibold text-[14px] text-[#667185] DMSans500">
              Design
            </p>
            <p class="font-bold text-[32px] text-[#86DC3D] DMSans500">73%</p>
            <div class="w-[154px] h-[5px] rounded-[4px] bg-[#86DC3D]"></div>
          </div>
        </div>
      </div>
      <div class="w-[1107px] h-[378px] flex flex-col justify-between">
        <div class="w-[1107px] h-[28px] text-[#101928] font-medium text-[20px]">
          Burnout Distribution
        </div>
        <div
          class="w-[1107px] h-[326px] border rounded-[8px] border-[#E4E7EC]"
        ></div>
      </div>
    </div>
    <div class="w-[1107px] h-[411px] flex justify-between">
      <div class="w-[541.5px] h-[411px] flex flex-col justify-between">
        <div class="flex justify-between">
          <p class="font-medium text-[#101828] text-[20px]">Burnout Alerts</p>
          <!-- <div class="w-[316px] h-[40px] flex justify-end"> -->
          <button
            class="border-[#ACCBEC] text-[#2F7DD0] w-[115px] h-[40px] font-semibold flex items-center justify-center gap-[8px] rounded-[4px] border"
          >
            <img
              src="/assets/icons/ArrowUpRight.png"
              alt=""
              class="h-[16px] w-[16px]"
            />
            View all
          </button>
          <!-- </div> -->
        </div>
        <div
          class="w-[541.5px] h-[347px] p-[24px] flex flex-col gap-[14px] border-[#E4E7EC] rounded-[8px] border bg-[#FCFCFC] items-center"
        >
          <div
            class="bg-white w-full h-full rounded-[8px] p-[10px] border border-[#E4E7EC] flex items-center flex-col"
          >
            <div
              class="w-[429.5px] h-[60px] px-[19px] py-[7px] items-start flex justify-between bg-white border-b mb-[7px]"
            >
              <div class="flex gap-[4px]">
                <img
                  src="/assets/css/avatar.png"
                  alt=""
                  class="w-[46px] h-[46px] rounded-full"
                />
                <div class="h-[49px] flex flex-col">
                  <p class="text-[14px] text-[#667185] font-medium DMSans500">
                    Amaka Onochie
                  </p>
                  <div class="text-[12px] DMSans400">
                    <p
                      class="text-[#853C90] text-[12px] DMSans400 font-semibold bg-[#F6EDF8] py-[4px] px-[10px] rounded-[16px] w-[58px]"
                    >
                      Design
                    </p>
                  </div>
                </div>
              </div>
              <div
                class="bg-[#FCEFE9] text-[#B34C19] text-[12px] DMSans500 rounded-[16px] h-[25px] px-[8px] py-[2px] flex gap-[4px] items-center"
              >
                <span class="text-[30px] text-[#B34C19]">&#8226;</span> Due for
                leave
              </div>
            </div>
            <div
              class="w-[429.5px] h-[60px] bg-white px-[19px] py-[7px] items-start flex justify-between border-b"
            >
              <div class="flex gap-[4px]">
                <img
                  src="/assets/css/avatar.png"
                  alt=""
                  class="w-[46px] h-[46px] rounded-full"
                />
                <div class="h-[49px] flex flex-col">
                  <p class="text-[14px] text-[#667185] font-medium DMSans500">
                    Amaka Onochie
                  </p>
                  <div class="text-[12px] DMSans400">
                    <p
                      class="text-[#853C90] text-[12px] DMSans400 font-semibold bg-[#F6EDF8] py-[4px] px-[10px] rounded-[16px] w-[58px]"
                    >
                      Design
                    </p>
                  </div>
                </div>
              </div>
              <div
                class="bg-[#FCEFE9] text-[#B34C19] text-[12px] DMSans500 rounded-[16px] h-[25px] px-[8px] py-[2px] flex gap-[4px] items-center"
              >
                <span class="text-[30px] text-[#B34C19]">&#8226;</span> Due for
                leave
              </div>
            </div>
          </div>
        </div>
      </div>
      .
      <div class="w-[541.5px] h-[411px] flex flex-col justify-between">
        <div class="flex justify-between">
          <p class="font-medium text-[#101828] text-[20px]">Members on Leave</p>
          <!-- <div class="w-[316px] h-[40px] flex justify-end"> -->
          <button
            class="border-[#ACCBEC] text-[#2F7DD0] w-[115px] h-[40px] font-semibold flex items-center justify-center gap-[8px] rounded-[4px] border"
          >
            <img
              src="/assets/icons/ArrowUpRight.png"
              alt=""
              class="h-[16px] w-[16px]"
            />
            View all
          </button>
          <!-- </div> -->
        </div>
        <div
          class="w-[541.5px] h-[347px] p-[24px] flex flex-col gap-[14px] border-[#E4E7EC] rounded-[8px] border bg-[#FCFCFC] items-center"
        >
          <div
            class="bg-white w-full h-full rounded-[8px] p-[10px] border border-[#E4E7EC] flex items-center flex-col"
          >
            <div
              class="w-[429.5px] h-[60px] px-[19px] py-[7px] items-start flex justify-between bg-white border-b mb-[7px]"
            >
              <div class="flex gap-[4px]">
                <img
                  src="/assets/css/avatar.png"
                  alt=""
                  class="w-[46px] h-[46px] rounded-full"
                />
                <div class="h-[49px] flex flex-col">
                  <p class="text-[14px] text-[#667185] font-medium DMSans500">
                    Amaka Onochie
                  </p>
                  <div class="text-[12px] DMSans400">
                    <p
                      class="text-[#853C90] text-[12px] DMSans400 font-semibold bg-[#F6EDF8] py-[4px] px-[10px] rounded-[16px] w-[58px]"
                    >
                      Design
                    </p>
                  </div>
                </div>
              </div>
              <div
                class="bg-[#F0F2F5] text-[#667185] text-[12px] DMSans500 rounded-[16px] h-[25px] px-[8px] py-[2px] flex gap-[4px] items-center"
              >
                <span class="text-[30px] text-[#667185]">&#8226;</span> Burnout
                Break
              </div>
            </div>
            <div
              class="w-[429.5px] h-[60px] bg-white px-[19px] py-[7px] items-start flex justify-between border-b"
            >
              <div class="flex gap-[4px]">
                <img
                  src="/assets/css/avatar.png"
                  alt=""
                  class="w-[46px] h-[46px] rounded-full"
                />
                <div class="h-[49px] flex flex-col">
                  <p class="text-[14px] text-[#667185] font-medium DMSans500">
                    Amaka Onochie
                  </p>
                  <div class="text-[12px] DMSans400">
                    <p
                      class="text-[#853C90] text-[12px] DMSans400 font-semibold bg-[#F6EDF8] py-[4px] px-[10px] rounded-[16px] w-[58px]"
                    >
                      Design
                    </p>
                  </div>
                </div>
              </div>
              <div
                class="bg-[#FCEFE9] text-[#B34C19] text-[12px] DMSans500 rounded-[16px] h-[25px] px-[8px] py-[2px] flex gap-[4px] items-center"
              >
                <span class="text-[30px] text-[#B34C19]">&#8226;</span> Due for
                leave
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div v-if="isInviteNewMember">
    <InviteNewMemberModal @closeModal="cancelInviteNewMemberModal" />
  </div>
</template>
<script setup>
import { useToast } from "vue-toastification";

const toast = useToast();
const userDetails = ref("");
const isInviteNewMember = ref(false);
const baseURL = useRuntimeConfig().public.baseURL;
const isDateClicked = ref(false);
const dateBtnClicked = () => {
  isDateClicked.value = !isDateClicked.value;
};
const inviteMembers = () => {
  isInviteNewMember.value = true;
};
const cancelInviteNewMemberModal = (value) => {
  isInviteNewMember.value = value;
};
const userTeamDetails = useCookie("userTeamDetails");
console.log(userTeamDetails.value);
const { data } = await useFetch(`${baseURL}/users/all`, {
  method: "get",
  headers: {
    Authorization: `Bearer ${userTeamDetails.value.access_token}`,
  },
});

  const totalMembers = data.value?.total ;
  console.log( totalMembers);

// const userTeamDetails = useCookie("userTeamDetails");
// console.log(userTeamDetails.value);
// const { data: page } = await useFetch(`${baseURL}/users/all?page=2`, {
//   method: "get",
//   headers: {
//     Authorization: `Bearer ${userTeamDetails.value.access_token}`,
//   },
// });
// console.log(page.value);
console.log(data.value);
</script>
