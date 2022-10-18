<template>
    <section :class="sidebarOpenActive ? 'w-[0%]' : 'w-[100%]'"
        class="sidebarMobile relative duration-300">
        <div  v-if="sidebarOpenActive" @click="toggleSidebar()"
            class="addIcon z-[10] p-1  rounded-full cursor-pointer">
        <svg  xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1"  viewBox="0 0 256 256" xml:space="preserve">
        
            <defs>
            </defs>
            <g style="stroke: none; stroke-width: 0; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill: none; fill-rule: nonzero; opacity: 1;"
                transform="translate(1.4065934065934016 1.4065934065934016) scale(2.81 2.81)">
                <path
                    d="M 37.882 90 c -0.338 0 -0.676 -0.086 -0.981 -0.258 c -0.629 -0.354 -1.019 -1.02 -1.019 -1.742 V 45.354 L 3.923 3.208 C 3.464 2.604 3.388 1.791 3.726 1.11 S 4.758 0 5.517 0 h 78.966 c 0.76 0 1.453 0.43 1.791 1.11 s 0.262 1.493 -0.197 2.098 L 54.118 45.354 V 79.37 c 0 0.699 -0.365 1.348 -0.963 1.71 l -14.237 8.63 C 38.601 89.903 38.241 90 37.882 90 z M 9.543 4 l 29.932 39.474 c 0.264 0.348 0.406 0.772 0.406 1.208 v 39.767 l 10.236 -6.205 V 44.682 c 0 -0.437 0.143 -0.861 0.406 -1.208 L 80.457 4 H 9.543 z M 52.118 79.37 h 0.01 H 52.118 z"
                    style="stroke: none; stroke-width: 1; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill: rgb(0,0,0); fill-rule: nonzero; opacity: 1;"
                    transform=" matrix(1 0 0 1 0 0) " stroke-linecap="round" />
            </g>
        </svg>
        </div>
        <div  v-if="!sidebarOpenActive" @click="toggleSidebar()"
            class="absolute z-[10] right-[9px] top-[45px] p-1 mainBackgroundColor rounded-full cursor-pointer">
        <svg width="24px" height="24px" style="fill: #fff;" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <g data-name="Layer 2">
                <g data-name="close">
                    <rect width="24" height="24" transform="rotate(180 12 12)" opacity="0" />
                    <path
                        d="M13.41 12l4.3-4.29a1 1 0 1 0-1.42-1.42L12 10.59l-4.29-4.3a1 1 0 0 0-1.42 1.42l4.3 4.29-4.3 4.29a1 1 0 0 0 0 1.42 1 1 0 0 0 1.42 0l4.29-4.3 4.29 4.3a1 1 0 0 0 1.42 0 1 1 0 0 0 0-1.42z" />
                </g>
            </g>
        </svg>
        </div>
<!-- Logo -->
        <div class="flex filter__logo">
            <img class="w-[70px] " src="@/assets/logotip.png" alt="logo" />
            <img :class="sidebarOpenActive ? 'opacity-0' : ''" class="duration-300 w-[170px] object-contain ml-4"
                src="../../assets/logo-text.png" alt="img" />
        </div>
<!-- Search Filters-->
<!-- By name         -->
<div v-if="!sidebarOpenActive" class="flex items-center rounded-[4px] mt-12 py-[15px] px-[25px] bg-[#F2F5F7]">        
    <span
                class="pr-[18px] border-r-[1.5px] border-[#111] border-opacity-[0.1] duration-300 cursor-pointer min-w-[50px]"
                :class="!sidebarOpenActive ? '' : 'border-opacity-0'">
                <search-icon stroke="stroke-[#BCC6D2]" width="23" height="23" />
            </span>
            <input type="text"
                class="w-full caret-[#5FC7D1] pl-[12px] bg-transparent focus:outline-none text-[#141839] placeholder:text-[#BCC6D2] text-[15px]"
                placeholder="Поиск по названию" :class="sidebarOpenActive ? 'opacity-0' : ''" />
        </div>
        <!--By Date -->
        <div v-if="!sidebarOpenActive" class="flex items-center rounded-[4px] mt-12 py-[15px] px-[25px] bg-[#F2F5F7]">
            <span class="pr-[18px] border-r-[1.5px] border-[#111] border-opacity-[0.1] duration-300 cursor-pointer min-w-[50px]"
                :class="!sidebarOpenActive ? '' : 'border-opacity-0'">
                <search-icon stroke="stroke-[#BCC6D2]" width="23" height="23" />
            </span>
            <input type="date"
                class="w-full caret-[#5FC7D1] pl-[12px] bg-transparent focus:outline-none text-[#141839] placeholder:text-[#BCC6D2] text-[15px]"
                placeholder="Поиск по дате" :class="sidebarOpenActive ? 'opacity-0' : ''" />
        </div>
        <!-- By howmany -->
            <div v-if="!sidebarOpenActive" class="flex items-center rounded-[4px] mt-12 py-[15px] px-[25px] bg-[#F2F5F7]">
                <span class="pr-[18px] border-r-[1.5px] border-[#111] border-opacity-[0.1] duration-300 cursor-pointer min-w-[50px]"
                    :class="!sidebarOpenActive ? '' : 'border-opacity-0'">
                    <search-icon stroke="stroke-[#BCC6D2]" width="23" height="23" />
                </span>
                <input type="number"
                    class="w-full caret-[#5FC7D1] pl-[12px] bg-transparent focus:outline-none text-[#141839] placeholder:text-[#BCC6D2] text-[15px]"
                    placeholder="Поиск по количеству" :class="sidebarOpenActive ? 'opacity-0' : ''" />
            </div>
            <!-- By price -->
                <div v-if="!sidebarOpenActive" class="flex items-center rounded-[4px] mt-12 py-[15px] px-[25px] bg-[#F2F5F7]">
                    <span class="pr-[18px] border-r-[1.5px] border-[#111] border-opacity-[0.1] duration-300 cursor-pointer min-w-[50px]"
                        :class="!sidebarOpenActive ? '' : 'border-opacity-0'">
                        <search-icon stroke="stroke-[#BCC6D2]" width="23" height="23" />
                    </span>
                    <input type="text"
                        class="w-full caret-[#5FC7D1] pl-[12px] bg-transparent focus:outline-none text-[#141839] placeholder:text-[#BCC6D2] text-[15px]"
                        placeholder="Поиск по цене" :class="sidebarOpenActive ? 'opacity-0' : ''" />
                </div>
                <div v-if="!sidebarOpenActive" @click="toggleSidebar()" class="flex items-center rounded-[4px] mt-12 py-[15px] px-[25px] filter__button">
                   <button>Фильтрация</button>
                </div>
    </section>
</template>

<script>
import { computed, ref } from "vue";
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
import { useRoute } from 'vue-router';
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
        const route = useRoute()
        const customers = computed(() => {
    return route.path === '/customers'
        })
        const orders = computed(() => {
            return route.path == '/orders'
        })
        const sale = computed(() => {
            return route.path == '/sale'
        })
        return {
            customers,
            sale,
            orders,
            route,
            toggleSidebar,
            sidebarOpenActive,
        };
    },
};
</script>

<style>

</style>
