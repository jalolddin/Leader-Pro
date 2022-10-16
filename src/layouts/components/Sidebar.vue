<template>
  <section
    :class="sidebarOpenActive ? 'w-[95px]' : 'w-[360px]'  "
    class="h-[100%] sidebar relative duration-300 px-[10px] py-[20px]"
    >
        <div @click="toggleSidebar()"
          class="absolute addIcon z-[10] right-[-86px] top-[35px] p-1 mainBackgroundColor rounded-full cursor-pointer">
          <img :class="sidebarOpenActive ? '' : 'rotate-180'" class="duration-300" src="../../assets/icons/smallArrow.svg"
            alt="image" />
        </div>
    <div  
      @click="toggleSidebar()"
      class="absolute z-[10] right-[-16px] top-[73px] p-1 mainBackgroundColor rounded-full cursor-pointer"
      >
      <img
        :class="sidebarOpenActive ? '' : 'rotate-180'"
        class="duration-300"
        src="../../assets/icons/smallArrow.svg"
        alt="image"
      />
    </div>

    <div class="flex">
      <img class="w-[70px]" src="@/assets/logotip.png" alt="logo" />
      <img
        :class="sidebarOpenActive ? 'opacity-0' : ''"
        class="duration-300 w-[170px] object-contain ml-4"
        src="../../assets/logo-text.png"
        alt="img"
      />
    </div>

    <div
    v-if="!sidebarOpenActive"
      class="flex items-center rounded-[4px] mt-12 py-[15px] px-[25px] bg-[#F2F5F7]"
    >
      <span
        class="pr-[18px] border-r-[1.5px] border-[#111] border-opacity-[0.1] duration-300 cursor-pointer min-w-[50px]"
        :class="!sidebarOpenActive ? '' : 'border-opacity-0'"
      >
        <search-icon stroke="stroke-[#BCC6D2]" width="23" height="23" />
      </span>
      <input
        type="text"
        class="w-full caret-[#5FC7D1] pl-[12px] bg-transparent focus:outline-none text-[#141839] placeholder:text-[#BCC6D2] text-[15px]"
        placeholder="Izlash"
        :class="sidebarOpenActive ? 'opacity-0' : ''"
      />
    </div>

    <div
      class="sidebarLinks w-full overflow-hidden mt-5"
      :class="sidebarOpenActive ? 'active' : ''"
    >
      <ul class="flex flex-col">
        <li class="hover:bg-[#F2F5F7] rounded-[4px] duration-300">
          <router-link :to="{ name: 'Finance' }">
            <ComputingIcon stroke="stroke-current" width="24" />
            <!--  <img src="@/assets/icons/sidebar/computing.svg" alt=""> -->
            <span class="duraton-500 ml-[18px]"> {{$t('finance')}} </span>
          </router-link>
        </li>
        <li class="hover:bg-[#F2F5F7] rounded-[4px] duration-300">
          <!--<router-link :to="{ name: 'Mattress' }">
            <FactoryIcon stroke="stroke-current" width="24" />
            <span class="duraton-500"> Tsehlar </span>
          </router-link>-->
          <ul class="uk-nav-default group" uk-nav="multiple: true">
            <li class="uk-parent">
              <a href="#"
                ><div
                  class="flex items-center w-full group-hover:text-[#141839]"
                >
                  <!-- <img src="@/assets/icons/sidebar/house-2.svg" alt=""> -->

                  <HouseIcon
                    stroke="stroke-current mr-4"
                    width="24"
                    style="min-width: 30px !important"
                  />
                  <span class="duraton-500 ml-[18px]">{{$t('storage')}}</span>
                </div>
                <span uk-nav-parent-icon></span
              ></a>
              <ul class="uk-nav-sub">
                <li
                  class="hover:bg-[#344566] hover:bg-opacity-[0.18] rounded-[4px] duration-300"
                >
                  <router-link :to="{ name: 'RawMaterial' }">
                    <!-- <img src="@/assets/icons/sidebar/glass.svg" alt="">-->
                    <GlassIcon style="min-width: 25px !important" />
                    <span class="duraton-500"> {{$t('raw')}} </span>
                  </router-link>
                </li>
                <li
                  class="hover:bg-[#344566] hover:bg-opacity-[0.18] rounded-[4px] duration-300"
                >
                  <router-link :to="{ name: 'Accessories' }">
                    <!-- <img src="@/assets/icons/sidebar/group.svg" alt="">-->

                    <AccessoriesIcon style="min-width: 24px !important" />
                    <span class="duraton-500"> {{$t('accessories')}} </span>
                  </router-link>
                </li>
                <li
                  class="hover:bg-[#344566] hover:bg-opacity-[0.18] rounded-[4px] duration-300"
                >
                  <router-link :to="{ name: 'Equipment' }">
                    <!-- <img src="@/assets/icons/sidebar/ruler&pen.svg" alt="">-->

                    <RullerIcon style="min-width: 25px !important" />
                    <span class="duraton-500"> {{$t('equipment')}} </span>
                  </router-link>
                </li>
                <li
                  class="hover:bg-[#344566] hover:bg-opacity-[0.18] rounded-[4px] duration-300"
                >
                  <router-link :to="{ name: 'Machines' }">
                    <!-- <img src="@/assets/icons/sidebar/group.svg" alt="">-->

                    <GroupIcon style="min-width: 25px !important" />
                    <span class="duraton-500"> {{$t('tech')}} </span>
                  </router-link>
                </li>
              </ul>
            </li>
          </ul>
        </li>
        <li class="hover:bg-[#F2F5F7] rounded-[4px] duration-300">
          <router-link :to="{ name: 'Production' }">
            <BucketSquareIcon style="min-width: 30px !important" />
            <!--  <img src="@/assets/icons/sidebar/computing.svg" alt=""> -->
            <span class="duraton-500 ml-[18px]">{{$t('production')}}</span>
          </router-link>
        </li>
        <li class="hover:bg-[#F2F5F7] rounded-[4px] duration-300">
          <!--<router-link :to="{ name: 'Mattress' }">
            <FactoryIcon stroke="stroke-current" width="24" />
            <span class="duraton-500"> Tsehlar </span>
          </router-link>-->
          <ul class="uk-nav-default group" uk-nav="multiple: true">
            <li class="uk-parent">
              <a href="#"
                ><div
                  class="flex items-center w-full group-hover:text-[#141839]"
                >
                  <FactoryIcon
                    stroke="stroke-current mr-4"
                    width="24"
                    style="min-width: 30px !important"
                  />
                  <span>{{$t('firms')}}</span>
                </div>
                <span uk-nav-parent-icon></span
              ></a>
              <ul class="uk-nav-sub">
                <!-- <li
                  class="hover:bg-[#344566] hover:bg-opacity-[0.18] rounded-[4px] duration-300"
                >
                  <router-link :to="{ name: 'FoamRubber' }">
                    <FoamRubberIcon style="min-width: 25px !important" />
                    <span class="duraton-500"> {{$t('foam')}} </span>
                  </router-link>
                </li> -->
                <li
                  class="hover:bg-[#344566] hover:bg-opacity-[0.18] rounded-[4px] duration-300"
                >
                  <router-link :to="{ name: 'Mattress' }">
                    <MatrasIcon style="min-width: 25px !important" />
                    <span class="duraton-500"> {{$t('mattress')}} </span>
                  </router-link>
                </li>
                <li
                  class="hover:bg-[#344566] hover:bg-opacity-[0.18] rounded-[4px] duration-300"
                >
                  <router-link :to="{ name: 'Pillow' }">
                    <PillowIcon style="min-width: 25px !important" />
                    <span class="duraton-500"> {{$t('pillow')}} </span>
                  </router-link>
                </li>
                <li
                  class="hover:bg-[#344566] hover:bg-opacity-[0.18] rounded-[4px] duration-300"
                >
                  <router-link :to="{ name: 'Sponge' }">
                    <SpongeIcon style="min-width: 25px !important" />
                    <span class="duraton-500"> {{$t('sponge')}} </span>
                  </router-link>
                </li>
                <li
                  class="hover:bg-[#344566] hover:bg-opacity-[0.18] rounded-[4px] duration-300"
                >
                  <router-link :to="{ name: 'CurlyCutting' }">
                    <CurlyCutting style="min-width: 25px !important" />
                    <span class="duraton-500"> {{$t('curly_cutting')}} </span>
                  </router-link>
                </li>
              </ul>
            </li>
          </ul>
        </li>
        <li class="hover:bg-[#F2F5F7] rounded-[4px] duration-300">
          <router-link :to="{ name: 'Sailing' }">
            <SailingHistory stroke="stroke-current" width="24" />
            <span class="duraton-500 ml-[18px]">{{$t('sales')}}</span>
          </router-link>
        </li>
        <li class="hover:bg-[#F2F5F7] rounded-[4px] duration-300">
          <router-link :to="{ name: 'Customers' }">
            <!-- <img src="@/assets/icons/sidebar/people.svg" alt="">-->
            <PeopleIcon stroke="stroke-current" width="24" />
            <span class="duraton-500 ml-[18px]">{{$t('clients')}}</span>
          </router-link>
        </li>
        <li class="hover:bg-[#F2F5F7] rounded-[4px] duration-300">
          <router-link :to="{ name: 'Orders' }">
            <!-- <img src="@/assets/icons/sidebar/calendar-edit.svg" alt=""> -->

            <CalendarEditIcon stroke="stroke-current" width="24" />
            <span class="duraton-500 ml-[18px]"> {{$t('orders')}} </span>
          </router-link>
        </li>
        <li class="hover:bg-[#F2F5F7] rounded-[4px] duration-300">
          <router-link :to="{ name: 'Admins' }">
            <AdminsIcon />
            <span class="duraton-500 ml-[18px]">{{$t('employees')}}</span>
          </router-link>
        </li>
      </ul>
    </div>

    <div  class="flex items-center cursor-pointer mainColorText px-[22px] py-[12px] hover:bg-[#F2F5F7] duration-300 rounded-[4px] mt-[70px]">
      <span><ExitIcon style="min-width: 25px" /></span>
      <span  :class="sidebarOpenActive ? 'opacity-0' : ''" class="ml-4">{{$t('exit')}}</span>
    </div>
  </section>
</template>

<script>
import { ref } from "vue";
import AccessoriesIcon from "../../assets/iconsVue/AccessoriesIcon.vue";
import AdminsIcon from "../../assets/iconsVue/AdminsIcon.vue";
import SailingHistory from "../../assets/iconsVue/SailingHistory.vue";
import FactoryIcon from "../../assets/iconsVue/FactoryIcon.vue";
import SearchIcon from "../../assets/iconsVue/SearchIcon.vue";
import FoamRubberIcon from "../../assets/iconsVue/FoamRubberIcon.vue";
import MatrasIcon from "../../assets/iconsVue/MatrasIcon.vue";
import PillowIcon from "../../assets/iconsVue/PillowIcon.vue";
import SpongeIcon from "../../assets/iconsVue/SpongeIcon.vue";
import CurlyCutting from "../../assets/iconsVue/CurlyCutting.vue";
import HouseIcon from "../../assets/iconsVue/HouseIcon.vue";
import ComputingIcon from "../../assets/iconsVue/ComutingIcon.vue";
import PeopleIcon from "../../assets/iconsVue/PeopleIcon.vue";
import CalendarEditIcon from "../../assets/iconsVue/CalendarEditIcon.vue";
import RullerIcon from "../../assets/iconsVue/RullerIcon.vue";
import GlassIcon from "../../assets/iconsVue/GlassIcon.vue";
import GroupIcon from "../../assets/iconsVue/GroupIcon.vue";
import ExitIcon from "../../assets/iconsVue/ExitIcon.vue";
import BucketSquareIcon from "../../assets/iconsVue/BucketSquareIcon.vue";
export default {
  components: {
    AccessoriesIcon,
    AdminsIcon,
    SearchIcon,
    SailingHistory,
    FactoryIcon,
    FoamRubberIcon,
    MatrasIcon,
    PillowIcon,
    SpongeIcon,
    CurlyCutting,
    HouseIcon,
    ComputingIcon,
    PeopleIcon,
    CalendarEditIcon,
    GroupIcon,
    GlassIcon,
    RullerIcon,
    ExitIcon,
    BucketSquareIcon,
  },
  setup() {
    let sidebarOpenActive = ref(true);
    const toggleSidebar = () => {
      sidebarOpenActive.value = !sidebarOpenActive.value;
    };

    return {
      toggleSidebar,
      sidebarOpenActive,
    };
  },
};
</script>

<style>

</style>
