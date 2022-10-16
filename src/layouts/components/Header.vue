<template>
<div>
  <div
    class="py-[20px] px-[30px] flex header items-center justify-between border-b-[1.5px] border-[#F2F5FA]"
  >
    <div>
      <!-- <img class="menuIcon" src="@/assets/menu.png" alt=""> -->
      <h1 class="mainTitle">{{ getHeaderTitle() }}</h1>
    </div>

    <div class="flex items-center header__buttons">
      <button
        @click="toggleModal()"
        class="mainBackgroundColor hover:scale-105 duration-300 text-white basicBtn mr-6 bg-[#2597DE] rounded-lg"
      >
        <PlusIcon stroke="stroke-current mr-2" />
        {{$t('raw_material_arrived')}}
      </button>
      <button
        @click="toggleSoldModal()"
        class="mainBackgroundColor hover:scale-105 duration-300 text-white basicBtn rounded-lg"
      >
        <PlusIcon stroke="stroke-current mr-2" />
        {{$t('there_was_sale')}}
      </button>
      <div class="w-[1.5px] line h-[40px] bg-[#F2F5FA] mx-6"></div>
      <button
        class="mainBackgroundColorYellow third_button hover:scale-105 duration-300 text-white basicBtn rounded-lg"
        @click="$router.push('/codebase')"
      >
        <!-- <PlusIcon stroke="stroke-current mr-2" /> -->
        <img src="@/assets/icons/navbar/element-plus.svg" class="mr-2" alt="">
        {{$t('codebase')}}
      </button>
      <!-- Icons -->
      <div class="w-[1.5px] line h-[40px] bg-[#F2F5FA] mx-6"></div>
      <div class="header__icons">

      <div class="cursor-pointer relative">
        <div ref="systemColorRef" class="absolute left-0 top-0 w-full h-full"></div>
          <SunIcon width="34" height="34" />

        <Dropdown>
          <template v-slot:dropdown>
            <div
              :class="
                isSystemDropdownActive
                  ? 'opacity-100 z-10 h-[97px]'
                  : 'opacity-0 z-[-1] h-0'
              "
              class="duration-300 absolute -right-3 top-14 mainBackgroundColorBlack rounded-[12px] w-[140px] overflow-y-scroll scroll-none"
            >
              <ul class="text-white flex flex-col space-y-2 py-1">
                <li
                  @click="handleLang('uz')"
                  class="flex items-center space-x-2 hover:bg-[#ffffff22] p-2"
                >
                  <MoonIcon fill="fill-[#8292AA]" />
                  <span>{{$t('dark')}}</span>
                </li>
                <li
                  @click="handleLang('ru')"
                  class="flex items-center space-x-2 hover:bg-[#ffffff22] p-2"
                >
                  <sun-icon stroke="stroke-[#8292AA]"></sun-icon>
                  <span>{{$t('light')}}</span>
                </li>
              </ul>
            </div>
          </template>
        </Dropdown>
      </div>
      <div class="relative ml-6">
        <img
          ref="nitificationRef"
          class="cursor-pointer"
          src="@/assets/icons/notification.svg"
          alt="img"
        />
        <Notification>
          <template v-slot:notification>
            <div
              :class="
                isNotificationDropdownActive
                  ? 'opacity-100 z-10 h-[180px]'
                  : 'opacity-0 z-[-1] h-0'
              "
              class="duration-300 absolute right-3 top-14 mainBackgroundColorBlack px-4 rounded-[12px] w-[400px] overflow-y-scroll scroll-none"
            >
              <ul class="relative">
                <li
                  v-for="index in 3"
                  class="py-4 border-b-[1.5px] border-white border-opacity-[0.4] relative flex items-center justify-between"
                  :key="index"
                >
                  <p class="text-white w-[70%]">
                    200ta 1 zichlik porolon sotildi
                  </p>

                  <span class="text-sm text-[#ffffffaa]">20.07.2022</span>
                </li>

                <div
                  class="z-[-1] w-[40px] h-[40px] mainBackgroundColorBlack rounded-[4px] absolute top-[-36px] -right-1 rotate-45"
                ></div>
              </ul>
            </div>
          </template>
        </Notification>
      </div>
      <!-- <img
        src="@/assets/man.png"
        ref="profileRef"
        class="ml-8 w-[40px] h-[40px] rounded-full flex items-center justify-center cursor-pointer"
        alt="avatar"
      /> -->
    </div>
    </div>
  </div>

  <ProfileDropdown v-if="profileDropdownActive" />

  <RawMaterialsAddModal :isModalActive="isModalActive"/>
  <SoldModal :isModalActive="isSoldModalActive" :modalWidth="600"/>

</div>
</template>

<script>
import { ref, onMounted, getCurrentInstance } from "vue";
import { useRouter, useRoute } from "vue-router";
import ProfileDropdown from "@/components/base/ProfileDropdown.vue";
import PlusIcon from "@/assets/iconsVue/PlusIcon.vue";
import Modal from "../../components/base/Modal.vue";
import Notification from "../../components/base/Notification.vue";
import SunIcon from "@/assets/iconsVue/SunIcon.vue";
import Dropdown from "@/components/base/Dropdown.vue";
import MoonIcon from "@/assets/iconsVue/MoonIcon.vue";
import { useI18n } from 'vue-i18n'
import RawMaterialsAddModal from './RawMaterialsAddModal.vue'
import SoldModal from './SoldModal.vue'
export default {
  components: {
    ProfileDropdown,
    PlusIcon,
    Modal,
    Notification,
    SunIcon,
    Dropdown,
    MoonIcon,


    RawMaterialsAddModal,
    SoldModal
  },
 
  setup() {
    const instance = getCurrentInstance();
    const globalVariables = instance.appContext.config.globalProperties;
    const router = useRouter();
    const route = useRoute();
    const { t } = useI18n()

    let isModalActive = ref(false);
    let isSoldModalActive = ref(false);
    let profileDropdownActive = ref(false);
    let isNotificationDropdownActive = ref(false);
    let isSystemDropdownActive = ref(false);


    const profileRef = ref(null);
    const nitificationRef = ref(null);
    const systemColorRef = ref(null);

    const toggleProfileDropdown = (e) => {
      if (e.target == profileRef.value) {
        profileDropdownActive.value = true;
      } else {
        profileDropdownActive.value = false;
      }

      if (e.target == nitificationRef.value) {
        isNotificationDropdownActive.value = true;
      } else {
        isNotificationDropdownActive.value = false;
      }

      if (e.target == systemColorRef.value) {
        isSystemDropdownActive.value = true;
      } else {
        isSystemDropdownActive.value = false;
      }
    };
    console.log(instance)
    function getHeaderTitle() {
      switch (route.name) {
        case "Admins":
          return globalVariables.$t('staff_admins');
        case "Profile":
          return globalVariables.$t('profile_settings');
        case "Factories":
          return globalVariables.$t('mattress');
        case "Pillow":
          return globalVariables.$t('pillow');
        case "Sponge":
          return globalVariables.$t('sponge');
        case "CurlyCutting":
          return globalVariables.$t('curly_cutting');
        case "Sailing":
          return globalVariables.$t('sales');
        case "RawMaterial":
          return globalVariables.$t('raw');
        case "Equipment":
          return globalVariables.$t('equipment');
        case "Machines":
          return globalVariables.$t('tech');
        case "Orders":
          return globalVariables.$t('orders');
        case "Customers":
          return globalVariables.$t('clients');
        default:
          return "LFR.uz";
      }
    }

    const toggleModal = () => {
      isModalActive.value = !isModalActive.value;
    };
    const toggleSoldModal = () => {
      isSoldModalActive.value = !isSoldModalActive.value;
    };

    const handleLang = (e) => {
      // console.log(e)
    }

    //  const toggleNotificaton = (e) => {
    //   // isNotificationDropdownActive.value = !isNotificationDropdownActive.value;

    // };

    onMounted(() => {
      window.addEventListener("click", toggleProfileDropdown);
    });

    return {
      getHeaderTitle,
      toggleProfileDropdown,
      profileDropdownActive,
      profileRef,
      
      isModalActive,
      isSoldModalActive,


      toggleModal,
      toggleSoldModal,


      isNotificationDropdownActive,
      nitificationRef,
      systemColorRef,
      isSystemDropdownActive,
      handleLang
    };
  },
};
</script>
