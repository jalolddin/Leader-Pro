<template>
    <section :class="sidebarOpenActive ? 'w-[0%]' : 'w-[100%]'"
        class="h-[258vh] sidebarMobile relative duration-300">
        <div  v-if="sidebarOpenActive" @click="toggleSidebar()"
            class="addIcon z-[10] p-1 mainBackgroundColor rounded-full cursor-pointer">
            <img :class="sidebarOpenActive ? '' : 'rotate-180'" class="duration-300"
                src="../../assets/icons/smallArrow.svg" alt="image" />
        </div>
        <div  v-if="!sidebarOpenActive" @click="toggleSidebar()"
            class="absolute z-[10] right-[9px] top-[45px] p-1 mainBackgroundColor rounded-full cursor-pointer">
            <img :class="sidebarOpenActive ? '' : 'rotate-180'" class="duration-300"
                src="../../assets/icons/smallArrow.svg" alt="image" />
        </div>

        <div class="flex">
            <img class="w-[70px]" src="@/assets/logotip.png" alt="logo" />
            <img :class="sidebarOpenActive ? 'opacity-0' : ''" class="duration-300 w-[170px] object-contain ml-4"
                src="../../assets/logo-text.png" alt="img" />
        </div>

        <div v-if="!sidebarOpenActive" class="flex items-center rounded-[4px] mt-12 py-[15px] px-[25px] bg-[#F2F5F7]">
            <span
                class="pr-[18px] border-r-[1.5px] border-[#111] border-opacity-[0.1] duration-300 cursor-pointer min-w-[50px]"
                :class="!sidebarOpenActive ? '' : 'border-opacity-0'">
                <search-icon stroke="stroke-[#BCC6D2]" width="23" height="23" />
            </span>
            <input type="text"
                class="w-full caret-[#5FC7D1] pl-[12px] bg-transparent focus:outline-none text-[#141839] placeholder:text-[#BCC6D2] text-[15px]"
                placeholder="Izlash" :class="sidebarOpenActive ? 'opacity-0' : ''" />
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
