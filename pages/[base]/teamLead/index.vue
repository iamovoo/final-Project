<template>
  <div class="hidden md:block">
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
        <img
          src="/assets/icons/CaretDown.png"
          alt=""
          class="w-[12px] h-[12px]"
        />
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
    <div class="w-[1107px] h-[1139px] flex flex-col gap-[24px]">
      <div class="w-[1107px] h-[176px] flex flex-col gap-[16px]">
        <div class="w-[1107px] h-[28px]">
          <p class="text-[20px] bricolage">{{id}} team statistics</p>
        </div>
        <div class="flex justify-between">
          <div
            class="w-[258px] h-[132px] p-[24px] flex flex-col gap-[24px] border"
          >
            <div class="w-[136px] h-[20px] text-[14px]">Total team members</div>
            <div class="w-[210px] h-[40px] flex justify-between items-center">
              <div class="text-[32px] font-bold bricolage">90</div>
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
            class="w-[258px] h-[132px] p-[24px] flex flex-col gap-[24px] border"
          >
            <div class="w-[169px] h-[20px] text-[14px]">
              Total burnt-out members
            </div>
            <div class="w-[210px] h-[40px] flex justify-between items-center">
              <div class="text-[32px] font-bold bricolage">10</div>
              <div
                class="w-[40px] h-[40px] overflow-hidden p-[10px] border-[#E26E6A] rounded-full border"
              >
                <img
                  src="/assets/icons/redUsers.png"
                  alt=""
                  class="object-contain w-[20px] h-[20px]"
                />
              </div>
            </div>
          </div>
          <div
            class="w-[258px] h-[132px] p-[24px] flex flex-col gap-[24px] border"
          >
            <div class="w-[172px] h-[20px] text-[14px]">
              Members nearing burnout
            </div>
            <div class="w-[210px] h-[40px] flex justify-between items-center">
              <div class="text-[32px] font-bold bricolage">90</div>
              <div
                class="w-[40px] h-[40px] overflow-hidden p-[10px] border-[#F9DFD2] rounded-full border"
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
            class="w-[258px] h-[132px] p-[24px] flex flex-col gap-[24px] border"
          >
            <div class="w-[121px] h-[20px] text-[14px]">Members on leave</div>
            <div class="w-[210px] h-[40px] flex justify-between items-center">
              <div class="text-[32px] font-bold bricolage">23</div>
              <div
                class="w-[40px] h-[40px] overflow-hidden p-[10px] border-[#D7E6F6] rounded-full border"
              >
                <img
                  src="/assets/icons/blueUsers.png"
                  alt=""
                  class="object-contain w-[20px] h-[20px]"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="h-[507px] w-[1107px] flex flex-col gap-[16px]">
        <div class="h-[40px] w-[1107px] justify-between flex items-center">
          <div class="h-[28px] text-[20px] font-medium bricolage">
            Burnout statistics(Design team)
          </div>
          <div
            class="w-[203px] h-[40px] bg-[#2F7DD0] text-[#F9FAFB] DMSans500 font-semibold text-[16px] flex items-center justify-center"
          >
            Manage team burnout
          </div>
        </div>
        <div class="flex justify-between">
          <div
            class="w-[348px] h-[451px] flex flex-col gap-[24px] justify-between border pb-[24px]"
          >
            <div
              class="h-[296px] w-[348px] p-[24px] flex flex-col items-center gap-[24px]"
            >
              <div class="h-[24px] w-[300px] text-[16px] DMSans500">
                Burnout Report
              </div>
              <div class="h-[200px] w-[200px] border"></div>
            </div>
            <div class="w-[348px] h-[104] px-[24px] flex flex-col gap-[8px]">
              <div class="w-[300px] h-[20px] flex justify-between items-center">
                <div
                  class="w-[158px] h-[20px] text-[#667185] text-[14px] DMSans400 flex gap-[4px] items-center"
                >
                  <span class="text-[30px] text-[#04802E]">&#8226;</span> Charged
                </div>
                <div class="w-[89px] h-[20px]">58 members</div>
              </div>
              <div class="w-[300px] h-[20px] flex justify-between items-center">
                <div
                  class="w-[163px] h-[20px] text-[#667185] text-[14px] DMSans400  flex gap-[4px] items-center"
                >
                 <span class="text-[30px] text-[#E67F4C]">&#8226;</span>  About to be Burnt Out
                </div>
                <div class="w-[89px] h-[20px]">58 members</div>
              </div>
              <div class="w-[300px] h-[20px] flex justify-between items-center">
                <div
                  class="w-[156px] h-[20px] text-[#667185] text-[14px] DMSans400  flex gap-[4px] items-center"
                >
                  <span class="text-[30px] text-[#667185]">&#8226;</span>  Burnout Break
                </div>
                <div class="w-[89px] h-[20px]">58 members</div>
              </div>
              <div class="w-[300px] h-[20px] flex justify-between items-center">
                <div
                  class="w-[156px] h-[20px] text-[#667185] text-[14px] DMSans400  flex gap-[4px] items-center"
                >
                 <span class="text-[30px] text-[#D42620]">&#8226;</span> Burnt Out
                </div>
                <div class="w-[89px] h-[20px]">58 members</div>
              </div>
            </div>
          </div>
          <div
            class="w-[348px] h-[451px] flex flex-col justify-center items-center gap-[16px] p-[20px] border"
          >
            <div class="w-[316px] h-[37px] flex border-b gap-[4px]">
              <div
                class="w-[196px] h-[20px] DMSans400 text-[14px] text-[#1D2739]"
              >
                Members nearing burnout
              </div>
              <div
                class="w-[23px] h-[25px] text-[#B34C19] bg-[#FCEFE9] rounded-[16px] text-[12px] font-medium flex items-center justify-center"
              >
                20
              </div>
            </div>
            <div class="w-[316px] h-[37px] flex border-b justify-between">
              <div class="h-[20px] DMSans400 text-[14px] text-[#667185]">
                Oluwaseun Adebayo
              </div>
              <div
                class="w-[126px] h-[25px] text-[#B34C19] bg-[#FCEFE9] rounded-[16px]"
              >
                Almost Burnt Out
              </div>
            </div>
            <div class="w-[316px] h-[37px] flex border-b justify-between">
              <div class="h-[20px] DMSans400 text-[14px] text-[#667185]">
                Oluwaseun Adebayo
              </div>
              <div
                class="w-[126px] h-[25px] text-[#B34C19] bg-[#FCEFE9] rounded-[16px]"
              >
                Almost Burnt Out
              </div>
            </div>
            <div class="w-[316px] h-[37px] flex border-b justify-between">
              <div class="h-[20px] DMSans400 text-[14px] text-[#667185]">
                Oluwaseun Adebayo
              </div>
              <div
                class="w-[126px] h-[25px] text-[#B34C19] bg-[#FCEFE9] rounded-[16px]"
              >
                Almost Burnt Out
              </div>
            </div>
            <div class="w-[316px] h-[37px] flex border-b justify-between">
              <div class="h-[20px] DMSans400 text-[14px] text-[#667185]">
                Oluwaseun Adebayo
              </div>
              <div
                class="w-[126px] h-[25px] text-[#B34C19] bg-[#FCEFE9] rounded-[16px]"
              >
                Almost Burnt Out
              </div>
            </div>
            <div class="w-[316px] h-[37px] flex border-b justify-between">
              <div class="h-[20px] DMSans400 text-[14px] text-[#667185]">
                Oluwaseun Adebayo
              </div>
              <div
                class="w-[126px] h-[25px] text-[#B34C19] bg-[#FCEFE9] rounded-[16px]"
              >
                Almost Burnt Out
              </div>
            </div>
            <div class="w-[316px] h-[37px] flex border-b justify-between">
              <div class="h-[20px] DMSans400 text-[14px] text-[#667185]">
                Oluwaseun Adebayo
              </div>
              <div
                class="w-[126px] h-[25px] text-[#B34C19] bg-[#FCEFE9] rounded-[16px]"
              >
                Almost Burnt Out
              </div>
            </div>
            <div class="w-[316px] h-[40px] flex justify-end">
              <button
                @click="showBurnOut"
                class="border-[#ACCBEC] text-[#2F7DD0] w-[115px] h-[40px] font-semibold flex items-center justify-center gap-[8px] rounded-[4px] border"
              >
                <img
                  src="/assets/icons/ArrowUpRight.png"
                  alt=""
                  class="h-[16px] w-[16px]"
                />
                View all
              </button>
            </div>
          </div>
          <div
            class="w-[348px] h-[451px] flex flex-col border p-[20px] justify-between"
          >
            <div
              class="text-[16px] DMSans500 font-medium text-[#475467] h-[24px] w-[128px]"
            >
              Team task status
            </div>
            <div class="w-[316px] h-[350px] flex flex-col gap-[16px]">
              <div
                class="w-[316px] h-[56px] py-[16px]"
                :class="isCaretUp ? 'border-b' : 'border'"
              >
                <div class="w-[316px] h-[24px] flex justify-between px-[16px]">
                  <div class="flex gap-[12px]">
                    <div
                      class="bg-[#D7E6F6] rounded-full h-[24px] w-[24px] flex justify-center items-center"
                    >
                      O
                    </div>
                    <div>Olamide Akintan</div>
                  </div>
                  <div
                    class="h-[20px] w-[20px]"
                    @click="isCaretUpClicked('Olamide Akintan')"
                  >
                    <img
                      v-if="isCaretUp === false"
                      src="/assets/icons/CaretUp.png"
                      alt=""
                      class="h-[20px] w-[20px]"
                    />
                    <img
                      v-else
                      src="/assets/icons/CaretDown.png"
                      alt=""
                      class="h-[20px] w-[20px]"
                    />
                  </div>
                </div>
              </div>
              <div v-if="isCaretUp">
                <div
                  class="h-[117px] w-[316px] px-[16px] flex flex-col gap-[12px]"
                >
                  <div
                    class="flex justify-between items-center h-[20px] w-[284px]"
                  >
                    <div class="text-[#667185] text-[14px]">Task</div>
                    <div
                      class="text-[#1D2739] font-medium text-[14px] DMSans500"
                    >
                      Design left navigation
                    </div>
                  </div>
                  <div
                    class="flex justify-between items-center h-[20px] w-[284px]"
                  >
                    <div class="text-[#667185] text-[14px]">
                      Difficulty level
                    </div>
                    <div
                      class="text-[#1D2739] font-medium text-[14px] DMSans500"
                    >
                      02
                    </div>
                  </div>
                  <div
                    class="flex justify-between items-center h-[20px] w-[284px]"
                  >
                    <div class="text-[#667185] text-[14px]">Status</div>
                    <div
                      class="text-[#04802E] font-medium text-[14px] DMSans500 bg-[#ECFDF3]"
                    >
                      in progress
                    </div>
                  </div>
                  <div
                    class="flex justify-between items-center h-[20px] w-[284px]"
                  >
                    <div class="text-[#667185] text-[14px]">Burnout points</div>
                    <div
                      class="text-[#1D2739] font-medium text-[14px] DMSans500"
                    >
                      4
                    </div>
                  </div>
                </div>
              </div>
              <div
                class="w-[316px] h-[56px] py-[16px]"
                :class="isCaretUp1 ? 'border-b' : 'border'"
              >
                <div class="w-[316px] h-[24px] flex justify-between px-[16px]">
                  <div class="flex gap-[12px]">
                    <div
                      class="bg-[#D7E6F6] rounded-full h-[24px] w-[24px] flex justify-center items-center"
                    >
                      A
                    </div>
                    <div>Temitope Ige</div>
                  </div>
                  <div
                    class="h-[20px] w-[20px]"
                    @click="isCaretUpClicked('Temitope Ige')"
                  >
                    <img
                      v-if="isCaretUp1 === false"
                      src="/assets/icons/CaretUp.png"
                      alt=""
                      class="h-[20px] w-[20px]"
                    />
                    <img
                      v-else
                      src="/assets/icons/CaretDown.png"
                      alt=""
                      class="h-[20px] w-[20px]"
                    />
                  </div>
                </div>
              </div>
              <div v-if="isCaretUp1">
                <div
                  class="h-[117px] w-[316px] px-[16px] flex flex-col gap-[12px]"
                >
                  <div
                    class="flex justify-between items-center h-[20px] w-[284px]"
                  >
                    <div class="text-[#667185] text-[14px]">Task</div>
                    <div
                      class="text-[#1D2739] font-medium text-[14px] DMSans500"
                    >
                      Design left navigation
                    </div>
                  </div>
                  <div
                    class="flex justify-between items-center h-[20px] w-[284px]"
                  >
                    <div class="text-[#667185] text-[14px]">
                      Difficulty level
                    </div>
                    <div
                      class="text-[#1D2739] font-medium text-[14px] DMSans500"
                    >
                      02
                    </div>
                  </div>
                  <div
                    class="flex justify-between items-center h-[20px] w-[284px]"
                  >
                    <div class="text-[#667185] text-[14px]">Status</div>
                    <div
                      class="text-[#04802E] font-medium text-[14px] DMSans500 bg-[#ECFDF3]"
                    >
                      in progress
                    </div>
                  </div>
                  <div
                    class="flex justify-between items-center h-[20px] w-[284px]"
                  >
                    <div class="text-[#667185] text-[14px]">Burnout points</div>
                    <div
                      class="text-[#1D2739] font-medium text-[14px] DMSans500"
                    >
                      4
                    </div>
                  </div>
                </div>
              </div>
              <div
                class="w-[316px] h-[56px] py-[16px]"
                :class="isCaretUp2 ? 'border-b' : 'border'"
              >
                <div class="w-[316px] h-[24px] flex justify-between px-[16px]">
                  <div class="flex gap-[12px]">
                    <div
                      class="bg-[#D7E6F6] rounded-full h-[24px] w-[24px] flex justify-center items-center"
                    >
                      M
                    </div>
                    <div>Chinwe Okeke</div>
                  </div>
                  <div
                    class="h-[20px] w-[20px]"
                    @click="isCaretUpClicked('Chinwe Okeke')"
                  >
                    <img
                      v-if="isCaretUp2 === false"
                      src="/assets/icons/CaretUp.png"
                      alt=""
                      class="h-[20px] w-[20px]"
                    />
                    <img
                      v-else
                      src="/assets/icons/CaretDown.png"
                      alt=""
                      class="h-[20px] w-[20px]"
                    />
                  </div>
                </div>
              </div>
              <div v-if="isCaretUp2">
                <div
                  class="h-[117px] w-[316px] px-[16px] flex flex-col gap-[12px]"
                >
                  <div
                    class="flex justify-between items-center h-[20px] w-[284px]"
                  >
                    <div class="text-[#667185] text-[14px]">Task</div>
                    <div
                      class="text-[#1D2739] font-medium text-[14px] DMSans500"
                    >
                      Design left navigation
                    </div>
                  </div>
                  <div
                    class="flex justify-between items-center h-[20px] w-[284px]"
                  >
                    <div class="text-[#667185] text-[14px]">
                      Difficulty level
                    </div>
                    <div
                      class="text-[#1D2739] font-medium text-[14px] DMSans500"
                    >
                      02
                    </div>
                  </div>
                  <div
                    class="flex justify-between items-center h-[20px] w-[284px]"
                  >
                    <div class="text-[#667185] text-[14px]">Status</div>
                    <div
                      class="text-[#04802E] font-medium text-[14px] DMSans500 bg-[#ECFDF3]"
                    >
                      in progress
                    </div>
                  </div>
                  <div
                    class="flex justify-between items-center h-[20px] w-[284px]"
                  >
                    <div class="text-[#667185] text-[14px]">Burnout points</div>
                    <div
                      class="text-[#1D2739] font-medium text-[14px] DMSans500"
                    >
                      4
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div v-if="showBurnOutModal">
        <AlmostBurnoutModal @closeModal="closeModal" />
      </div>
      <BurnOutStats />
    </div>
  </div>
  <!-- <div class="block md:hidden">
    <div class="h-[60px] w-[375px] py-[16px] flex gap-[8px] border-b mb-[30px]">
      <div class="gap-[8px] flex justify-center items-center">
        <h6 class="font-medium text-[20px] bricolage text-[#101928]">
          Dashboard
        </h6>
        <div
          @click="dateBtnClicked"
          class="flex justify-center items-center w-[88px] h-[28px] gap-[4px] py-[4px] px-[8px] border border-[#E4E7EC] rounded-[2px]"
        >
          <img
            src="/assets/icons/CalendarBlank.png"
            alt=""
            class="w-[12px] h-[12px]"
          />
          <p class="text-[#667185] text-[14px] DMSans500">Today</p>
          <img
            src="/assets/icons/CaretDown.png"
            alt=""
            class="w-[12px] h-[12px]"
          />
        </div>
        <div
          class="absolute top-[51px] left-[108px] z-10 shadow-md bg-[#FFFFFF]"
          v-if="isDateClicked"
        >
          <div
            class="w-[200px] h-[200px] border py-[6px] px-[10px] z-10 bg-[#FFFFFF] rounded-[8px]"
          >
            <div class="w-[180px] h-[188px] py-[4px]">
              <div class="h-[36px] w-[180px] py-[8px] px-[16px]">
                <p class="text-[14px] DMSans400">Today</p>
              </div>
              <div class="h-[36px] w-[180px] py-[8px] px-[16px]">
                <p class="text-[14px] DMSans400">Last 7 Days</p>
              </div>
              <div class="h-[36px] w-[180px] py-[8px] px-[16px]">
                <p class="text-[14px] DMSans400">Last 30 Days</p>
              </div>
              <div class="h-[36px] w-[180px] py-[8px] px-[16px]">
                <p class="text-[14px] DMSans400">Last 3 Month</p>
              </div>
              <div class="h-[36px] w-[180px] py-[8px] px-[16px]">
                <p class="text-[14px] DMSans400">Last 12 Month</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="h-[3128px] w-[335px] flex-col gap-[24px]">
      <section class="h-[640px] w-[335px] flex flex-col gap-[24px]">
        <p class="text-[16px] text-[#101928]">Design team statistics</p>
        <div class="border h-[588px] w-[335px] flex flex-col gap-[20px]">
          <div
            class="w-[335px] h-[132px] p-[24px] flex flex-col gap-[24px] border"
          >
            <div class="w-[136px] h-[20px] text-[14px]">Total team members</div>
            <div class="w-[287px] h-[40px] flex justify-between items-center">
              <div class="text-[32px] font-bold bricolage">90</div>
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
            class="w-[335px] h-[132px] p-[24px] flex flex-col gap-[24px] border"
          >
            <div class="w-[169px] h-[20px] text-[14px]">
              Total burnt-out members
            </div>
            <div class="w-[287px] h-[40px] flex justify-between items-center">
              <div class="text-[32px] font-bold bricolage">10</div>
              <div
                class="w-[40px] h-[40px] overflow-hidden p-[10px] border-[#E26E6A] rounded-full border"
              >
                <img
                  src="/assets/icons/redUsers.png"
                  alt=""
                  class="object-contain w-[20px] h-[20px]"
                />
              </div>
            </div>
          </div>
          <div
            class="w-[335px] h-[132px] p-[24px] flex flex-col gap-[24px] border"
          >
            <div class="w-[172px] h-[20px] text-[14px]">
              Members nearing burnout
            </div>
            <div class="w-[287pxpx] h-[40px] flex justify-between items-center">
              <div class="text-[32px] font-bold bricolage">90</div>
              <div
                class="w-[40px] h-[40px] overflow-hidden p-[10px] border-[#F9DFD2] rounded-full border"
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
            class="w-[335px] h-[132px] p-[24px] flex flex-col gap-[24px] border"
          >
            <div class="w-[121px] h-[20px] text-[14px]">Members on leave</div>
            <div class="w-[287pxpx] h-[40px] flex justify-between items-center">
              <div class="text-[32px] font-bold bricolage">23</div>
              <div
                class="w-[40px] h-[40px] overflow-hidden p-[10px] border-[#D7E6F6] rounded-full border"
              >
                <img
                  src="/assets/icons/blueUsers.png"
                  alt=""
                  class="object-contain w-[20px] h-[20px]"
                />
              </div>
            </div>
          </div>
        </div>
      </section>
      <section class="h-[1408px] w-[335px] flex flex-col gap-[24px]">
        <div class="h-[68px] w-[335px] flex flex-col gap-[8px]">
          <h6 class="font-medium text-[16px] bricolage">
            Burnout statistics (Design team)
          </h6>
          <button
            class="bg-[#2F7DD0] text-[#F9FAFB] font-medium text-[14px] DMSans500 h-[32px] w-[170px] rounded-[4px]"
          >
            Manage team burnout
          </button>
        </div>
        <div
          class="w-[335px] h-[408px] flex flex-col justify-between border pb-[24px]"
        >
          <div
            class="h-[292px] w-[335px] p-[24px] flex flex-col justify-center items-center gap-[24px]"
          >
            <div class="h-[20px] w-[300px] text-[16px] DMSans500">
              Burnout Report
            </div>
            <div class="h-[200px] w-[200px] border"></div>
          </div>
          <div class="w-[335px] h-[92px] px-[24px] flex flex-col gap-[8px]">
            <div class="w-[287px] h-[17px] flex justify-between items-center">
              <div
                class="w-[158px] h-[17px] text-[#667185] text-[14px] DMSans400"
              >
                Charged
              </div>
              <div class="w-[89px] h-[17px]">58 members</div>
            </div>
            <div class="w-[287px] h-[17px] flex justify-between items-center">
              <div
                class="w-[163px] h-[17px] text-[#667185] text-[14px] DMSans400"
              >
                About to be Burnt Out
              </div>
              <div class="w-[89px] h-[17px]">58 members</div>
            </div>
            <div class="w-[287px] h-[17px] flex justify-between items-center">
              <div
                class="w-[156px] h-[17px] text-[#667185] text-[14px] DMSans400"
              >
                Burnout Break
              </div>
              <div class="w-[89px] h-[17px]">58 members</div>
            </div>
            <div class="w-[287px] h-[17px] flex justify-between items-center">
              <div
                class="w-[156px] h-[17px] text-[#667185] text-[14px] DMSans400"
              >
                Burnt Out
              </div>
              <div class="w-[89px] h-[17px]">58 members</div>
            </div>
          </div>
        </div>
        <div
          class="w-[335px] h-[451px] flex flex-col justify-center items-center gap-[16px] p-[20px] border rounded-[8px]"
        >
          <div class="w-[295px] h-[37px] flex border-b gap-[4px] pb-[12px]">
            <div
              class="w-[172px] h-[20px] DMSans400 text-[14px] text-[#1D2739]"
            >
              Members nearing burnout
            </div>
            <div
              class="w-[23px] h-[25px] text-[#B34C19] bg-[#FCEFE9] rounded-[16px] text-[12px] font-medium flex items-center justify-center"
            >
              20
            </div>
          </div>
          <div class="w-[295px] h-[37px] flex border-b justify-between">
            <div class="h-[20px] DMSans400 text-[12px] text-[#667185]">
              Oluwaseun Adebayo
            </div>
            <div
              class="w-[126px] h-[21px] text-[#B34C19] bg-[#FCEFE9] rounded-[16px] py-[2px] px-[8px] text-[12px]"
            >
              Almost Burnt Out
            </div>
          </div>
          <div class="w-[295px] h-[37px] flex border-b justify-between">
            <div class="h-[20px] DMSans400 text-[12px] text-[#667185]">
              Chinwe Okeke
            </div>
            <div
              class="w-[126px] h-[21px] text-[#B34C19] bg-[#FCEFE9] rounded-[16px] py-[2px] px-[8px] text-[12px]"
            >
              Almost Burnt Out
            </div>
          </div>
          <div class="w-[295px] h-[37px] flex border-b justify-between">
            <div class="h-[20px] DMSans400 text-[12px] text-[#667185]">
              Oluwaseun Adebayo
            </div>
            <div
              class="w-[126px] h-[21px] text-[#B34C19] bg-[#FCEFE9] rounded-[16px] py-[2px] px-[8px] text-[12px]"
            >
              Almost Burnt Out
            </div>
          </div>
          <div class="w-[295px] h-[37px] flex border-b justify-between">
            <div class="h-[20px] DMSans400 text-[12px] text-[#667185]">
              Chinwe Okeke
            </div>
            <div
              class="w-[126px] h-[21px] text-[#B34C19] bg-[#FCEFE9] rounded-[16px] py-[2px] px-[8px] text-[12px]"
            >
              Almost Burnt Out
            </div>
          </div>
          <div class="w-[295px] h-[37px] flex border-b justify-between">
            <div class="h-[20px] DMSans400 text-[12px] text-[#667185]">
              Oluwaseun Adebayo
            </div>
            <div
              class="w-[126px] h-[21px] text-[#B34C19] bg-[#FCEFE9] rounded-[16px] py-[2px] px-[8px] text-[12px]"
            >
              Almost Burnt Out
            </div>
          </div>
          <div class="w-[295px] h-[37px] flex border-b justify-between">
            <div class="h-[20px] DMSans400 text-[12px] text-[#667185]">
              Chinwe Okeke
            </div>
            <div
              class="w-[126px] h-[21px] text-[#B34C19] bg-[#FCEFE9] rounded-[16px] py-[2px] px-[8px] text-[12px]"
            >
              Almost Burnt Out
            </div>
          </div>
          <div class="w-[295px] h-[24px] flex justify-end">
            <button
              @click="showBurnOut"
              class="border-[#ACCBEC] text-[#2F7DD0] w-[79px] h-[24px] font-semibold flex items-center justify-center gap-[8px] rounded-[4px] border text-[12px]"
            >
              <img
                src="/assets/icons/ArrowUpRight.png"
                alt=""
                class="h-[16px] w-[16px]"
              />
              View all
            </button>
          </div>
        </div>
        <div
          class="w-[335px] h-[417px] p-[20px] flex flex-col gap-[16px] border"
        >
          <div
            class="text-[16px] DMSans500 font-medium text-[#475467] h-[24px] w-[128px]"
          >
            Team task status
          </div>
          <div class="w-[295px] h-[341px] flex flex-col gap-[16px]">
            <div
              class="w-[295px] h-[56px] py-[16px]"
              :class="isCaretUp ? 'border-b' : 'border'"
            >
              <div class="w-[295px] h-[24px] flex justify-between px-[16px]">
                <div class="flex gap-[12px]">
                  <div
                    class="bg-[#D7E6F6] rounded-full h-[24px] w-[24px] flex justify-center items-center"
                  >
                    O
                  </div>
                  <div>Olamide Akintan</div>
                </div>
                <div
                  class="h-[20px] w-[20px]"
                  @click="isCaretUpClicked('Olamide Akintan')"
                >
                  <img
                    v-if="isCaretUp === false"
                    src="/assets/icons/CaretUp.png"
                    alt=""
                    class="h-[20px] w-[20px]"
                  />
                  <img
                    v-else
                    src="/assets/icons/CaretDown.png"
                    alt=""
                    class="h-[20px] w-[20px]"
                  />
                </div>
              </div>
            </div>
            <div v-if="isCaretUp">
              <div
                class="h-[108px] w-[295px] px-[16px] flex flex-col gap-[12px]"
              >
                <div
                  class="flex justify-between items-center h-[20px] w-[284px]"
                >
                  <div class="text-[#667185] text-[14px]">Task</div>
                  <div class="text-[#1D2739] font-medium text-[14px] DMSans500">
                    Design left navigation
                  </div>
                </div>
                <div
                  class="flex justify-between items-center h-[20px] w-[284px]"
                >
                  <div class="text-[#667185] text-[14px]">Difficulty level</div>
                  <div class="text-[#1D2739] font-medium text-[14px] DMSans500">
                    02
                  </div>
                </div>
                <div
                  class="flex justify-between items-center h-[20px] w-[284px]"
                >
                  <div class="text-[#667185] text-[14px]">Status</div>
                  <div
                    class="text-[#04802E] font-medium text-[14px] DMSans500 bg-[#ECFDF3]"
                  >
                    in progress
                  </div>
                </div>
                <div
                  class="flex justify-between items-center h-[20px] w-[284px]"
                >
                  <div class="text-[#667185] text-[14px]">Burnout points</div>
                  <div class="text-[#1D2739] font-medium text-[14px] DMSans500">
                    4
                  </div>
                </div>
              </div>
            </div>
            <div
              class="w-[295px] h-[56px] py-[16px]"
              :class="isCaretUp1 ? 'border-b' : 'border'"
            >
              <div class="w-[295px] h-[24px] flex justify-between px-[16px]">
                <div class="flex gap-[12px]">
                  <div
                    class="bg-[#D7E6F6] rounded-full h-[24px] w-[24px] flex justify-center items-center"
                  >
                    A
                  </div>
                  <div>Temitope Ige</div>
                </div>
                <div
                  class="h-[20px] w-[20px]"
                  @click="isCaretUpClicked('Temitope Ige')"
                >
                  <img
                    v-if="isCaretUp1 === false"
                    src="/assets/icons/CaretUp.png"
                    alt=""
                    class="h-[20px] w-[20px]"
                  />
                  <img
                    v-else
                    src="/assets/icons/CaretDown.png"
                    alt=""
                    class="h-[20px] w-[20px]"
                  />
                </div>
              </div>
            </div>
            <div v-if="isCaretUp1">
              <div
                class="h-[108px] w-[295px] px-[16px] flex flex-col gap-[12px]"
              >
                <div
                  class="flex justify-between items-center h-[20px] w-[284px]"
                >
                  <div class="text-[#667185] text-[14px]">Task</div>
                  <div class="text-[#1D2739] font-medium text-[14px] DMSans500">
                    Design left navigation
                  </div>
                </div>
                <div
                  class="flex justify-between items-center h-[20px] w-[284px]"
                >
                  <div class="text-[#667185] text-[14px]">Difficulty level</div>
                  <div class="text-[#1D2739] font-medium text-[14px] DMSans500">
                    02
                  </div>
                </div>
                <div
                  class="flex justify-between items-center h-[20px] w-[284px]"
                >
                  <div class="text-[#667185] text-[14px]">Status</div>
                  <div
                    class="text-[#04802E] font-medium text-[14px] DMSans500 bg-[#ECFDF3]"
                  >
                    in progress
                  </div>
                </div>
                <div
                  class="flex justify-between items-center h-[20px] w-[284px]"
                >
                  <div class="text-[#667185] text-[14px]">Burnout points</div>
                  <div class="text-[#1D2739] font-medium text-[14px] DMSans500">
                    4
                  </div>
                </div>
              </div>
            </div>
            <div
              class="w-[295px] h-[56px] py-[16px]"
              :class="isCaretUp2 ? 'border-b' : 'border'"
            >
              <div class="w-[295px] h-[24px] flex justify-between px-[16px]">
                <div class="flex gap-[12px]">
                  <div
                    class="bg-[#D7E6F6] rounded-full h-[24px] w-[24px] flex justify-center items-center"
                  >
                    M
                  </div>
                  <div>Chinwe Okeke</div>
                </div>
                <div
                  class="h-[20px] w-[20px]"
                  @click="isCaretUpClicked('Chinwe Okeke')"
                >
                  <img
                    v-if="isCaretUp2 === false"
                    src="/assets/icons/CaretUp.png"
                    alt=""
                    class="h-[20px] w-[20px]"
                  />
                  <img
                    v-else
                    src="/assets/icons/CaretDown.png"
                    alt=""
                    class="h-[20px] w-[20px]"
                  />
                </div>
              </div>
            </div>
            <div v-if="isCaretUp2">
              <div
                class="h-[108px] w-[295px] px-[16px] flex flex-col gap-[12px]"
              >
                <div
                  class="flex justify-between items-center h-[20px] w-[284px]"
                >
                  <div class="text-[#667185] text-[14px]">Task</div>
                  <div class="text-[#1D2739] font-medium text-[14px] DMSans500">
                    Design left navigation
                  </div>
                </div>
                <div
                  class="flex justify-between items-center h-[20px] w-[284px]"
                >
                  <div class="text-[#667185] text-[14px]">Difficulty level</div>
                  <div class="text-[#1D2739] font-medium text-[14px] DMSans500">
                    02
                  </div>
                </div>
                <div
                  class="flex justify-between items-center h-[20px] w-[284px]"
                >
                  <div class="text-[#667185] text-[14px]">Status</div>
                  <div
                    class="text-[#04802E] font-medium text-[14px] DMSans500 bg-[#ECFDF3]"
                  >
                    in progress
                  </div>
                </div>
                <div
                  class="flex justify-between items-center h-[20px] w-[284px]"
                >
                  <div class="text-[#667185] text-[14px]">Burnout points</div>
                  <div class="text-[#1D2739] font-medium text-[14px] DMSans500">
                    4
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
      <div v-if="showBurnOutModal">
        <AlmostBurnoutModal @closeModal="closeModal" />
      </div>
      <BurnOutStats />
    </div>
  </div> -->
</template>
<script setup>
const {id} = useRoute().params
const isCaretUp = ref(false);
const isCaretUp1 = ref(false);
const isCaretUp2 = ref(false);
const showBurnOutModal = ref(false);
const name = ref("");
const isCaretUpClicked = (Fname) => {
  name.value = Fname;
  if (name.value === "Chinwe Okeke") {
    isCaretUp2.value = !isCaretUp2.value;
    isCaretUp.value = false;
    isCaretUp1.value = false;
  } else if (name.value === "Temitope Ige") {
    isCaretUp1.value = !isCaretUp1.value;
    isCaretUp2.value = false;
    isCaretUp.value = false;
  } else if (name.value === "Olamide Akintan") {
    isCaretUp.value = !isCaretUp.value;
    isCaretUp1.value = false;
    isCaretUp2.value = false;
  }
  console.log(name.value);
};
const showBurnOut = () => {
  showBurnOutModal.value = true;
};
const closeModal = (value) => {
  showBurnOutModal.value = value;
};
const isDateClicked = ref(false);
const dateBtnClicked = () => {
  isDateClicked.value = !isDateClicked.value;
};
const baseURL = useRuntimeConfig().public.baseURL
</script>
