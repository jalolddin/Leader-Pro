<template>
<section class="flex wrapperAll">
    <SidebarMobile class="sidebarMobile" />
    <Sidebar class="sidebarActive" />
    <div :class="{'-z-0': true}" class="flex das flex-col w-full border-l-[1.5px] border-[#F2F5FA]">
        <Header />
        <FooterPages class="footerPages"/>
        <router-view />
    </div>
</section>
</template>

<script>

import Header from '../layouts/components/Header.vue'
import Sidebar from '../layouts/components/Sidebar.vue'
import SidebarMobile from '../layouts/components/SidebarMobile.vue'
import FooterPages from './components/FooterPages.vue'
export default {
    components: {
    Sidebar,
    Header,
    SidebarMobile,
    FooterPages
},
}
</script>

<style scoped>
@media screen and (max-width: 490px) {
.sidebarActive{
    display: none;
}
}
@media screen and (min-width: 490px) {
    .sidebarMobile {
        display: none;
    }
        .footerPages{
display: none;
        }
}
</style>
