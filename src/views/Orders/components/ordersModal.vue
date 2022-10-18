<template>
     <div class="orders__modal">
     <h3 class="text-lg font-medium text-center main-color-black">
        {{$t('add_order')}}
      </h3>
      <div class="mt-4 space-y-3">
        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="@/assets/icons/allMoney.svg"
            alt="user"
          />
          <Datepicker v-model="date" :placeholder="$t('date')"></Datepicker>
        </div>


        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="@/assets/icons/allMoney.svg"
            alt="user"
          />
          <input
            type="text"
            name="text"
            autocomplete="off"
            required
            :placeholder="$t('clients_num')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
          />
        </div>



        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="@/assets/icons/allMoney.svg"
            alt="user"
          />
          <input
            type="text"
            name="text"
            autocomplete="off"
            required
            :placeholder="$t('fullname')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
          />
        </div>



        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="@/assets/icons/allMoney.svg"
            alt="user"
          />
          <input
            type="text"
            name="text"
            autocomplete="off"
            required
            :placeholder="$t('phone_number')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
          />
        </div>


        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="@/assets/icons/allMoney.svg"
            alt="user"
          />
          <input
            type="text"
            name="text"
            autocomplete="off"
            required
            :placeholder="$t('order_name')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
          />
        </div>



        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="@/assets/icons/allMoney.svg"
            alt="user"
          />
          <input
            type="text"
            name="text"
            autocomplete="off"
            required
            :placeholder="$t('order_number')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
          />
        </div>



        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="@/assets/icons/allMoney.svg"
            alt="user"
          />
          <input
            type="text"
            name="text"
            autocomplete="off"
            required
            :placeholder="$t('price_per_item')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
          />
        </div>


        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="@/assets/icons/allMoney.svg"
            alt="user"
          />
          <input
            type="text"
            name="text"
            autocomplete="off"
            required
            :placeholder="$t('total_sum')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
          />
        </div>
      </div>
          <div class="sold__modal__buttons">
          
            <button @click="goBack()">
              Отмена
            </button>
          
            <button>Потвердить</button>
          </div>
      </div>
</template>

<script>
import { getCurrentInstance } from "vue";
import { ref, onMounted, reactive } from "vue";
import { useRouter, useRoute } from "vue-router";
import PlusIcon from "@/assets/iconsVue/PlusIcon.vue";
import Modal from "@/components/base/Modal.vue";
import Notification from "@/components/base/Notification.vue";
import SunIcon from "@/assets/iconsVue/SunIcon.vue";
import Dropdown from "@/components/base/Dropdown.vue";
import MoonIcon from "@/assets/iconsVue/MoonIcon.vue";

export default {
    props: {
        isModalActive: {
            type: [Boolean],
            required: true,
        }
    },
    components: {
        PlusIcon,
        Modal,
        Notification,
        SunIcon,
        Dropdown,
        MoonIcon,

    },
    setup() {
        const instance = getCurrentInstance();
        const router = useRouter();
        const route = useRoute();
      
        const toggleModal = () => {
            instance.parent.setupState.toggleModal()
            // isModalActive.value = !isModalActive.value;
        };
        onMounted(() => {

        });
      const goBack = () => {
        router.go(-1)
      }
        return {
          toggleModal,
          goBack
        };
    }
}
</script>

<style>

</style>