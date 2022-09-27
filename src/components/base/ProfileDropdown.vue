<template>
<div class="profileDropdown w-[260px] px-6 rounded-[12px] shadow-xl border absolute top-[80px] right-[30px] duration-300">
    <ul class="flex flex-col">
        <li>
            <router-link :to="{ name: 'Profile' }">
                <span class="flex justify-between py-4 group text-lg">
                    {{$t('profile')}}
                    <SmallArrowRight stroke="stroke-current" class="group-hover:mr-0 mr-2 duration-200" />
                </span>
            </router-link>
        </li>
        <li>
            <router-link :to="{ name: 'Roles' }">
                <span class="flex justify-between py-4 group text-lg">
                    {{$t('roles')}}
                    <SmallArrowRight stroke="stroke-current" class="group-hover:mr-0 mr-2 duration-200" />
                </span>
            </router-link>
        </li>
        <li>
            <router-link :to="{ name: 'Permissions' }">
                <span class="flex justify-between py-4 group text-lg">
                    {{$t('permissions')}}
                    <SmallArrowRight stroke="stroke-current" class="group-hover:mr-0 mr-2 duration-200" />
                </span>
            </router-link>
        </li>
        <li>
            <router-link :to="{ name: 'Users' }">
                <span class="flex justify-between py-4 group text-lg">
                    {{$t('users')}}
                    <SmallArrowRight stroke="stroke-current" class="group-hover:mr-0 mr-2 duration-200" />
                </span>
            </router-link>
        </li>
    </ul>
</div>
</template>

<script>
import SmallArrowRight from '../../assets/iconsVue/SmallArrowRight.vue'
export default {
    components: {
        SmallArrowRight
    },
    setup() {

    }
}
</script>
