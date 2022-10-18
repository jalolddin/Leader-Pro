<template>
  <div class="footer">
    <ul class="footer__pages">
        <!-- Sales -->
            <li class="footer__sales">
                <router-link :to="{ name: 'Sailing' }">
                    <SailingHistory stroke="stroke-current" width="24" />
                    <span>{{$t('sales')}}</span>
                </router-link>
            </li>
            <!-- Orders -->
            <li class="footer__orders">
                <router-link :to="{ name: 'Orders' }">
                    <!-- <img src="@/assets/icons/sidebar/calendar-edit.svg" alt=""> -->
            
                    <CalendarEditIcon stroke="stroke-current" width="24" />
                    <span> {{$t('orders')}} </span>
                </router-link>
            </li>
            <!-- PlusIcon -->
            <li class="footer__plus">
                    <router-link :to="{ name: 'Modal' }">
                    <!-- <img src="@/assets/icons/sidebar/calendar-edit.svg" alt=""> -->
                    <PlusIcon stroke="stroke-current" width="40" />
                    
                </router-link>
                </li>
            <!-- Client -->
            <li class="footer__client">
                <router-link :to="{ name: 'Customers' }">
                    <!-- <img src="@/assets/icons/sidebar/people.svg" alt="">-->
                    <PeopleIcon stroke="stroke-current" width="24" />
                    <span>{{$t('clients')}}</span>
                </router-link>
            </li>
            <!-- Profile -->
                <li class="footer__profile">
                    <router-link :to="{ name: 'Profile' }">
                        <AdminsIcon stroke="stroke-current" width="24" />
                        <span>
                            {{$t('profile')}}
                        </span>
                    </router-link>
                </li>
    </ul>
  </div>
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
import PlusIcon from "../../assets/iconsVue/PlusIcon.vue";
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
    PlusIcon  
    },
}
</script>

<style>

</style>