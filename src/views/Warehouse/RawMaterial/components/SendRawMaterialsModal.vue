<template>
   <Modal :isModalActive="isModalActive" @close="toggleModal">

    <template v-slot:modalHeader>
      <h3 class="text-lg font-medium text-center main-color-black">
        {{$t('foam_production')}}
      </h3>
    </template>

    <template v-slot:modalBody>
      <div class="mt-4 space-y-3">
        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="@/assets/icons/allMoney.svg"
            alt="user"
          />
          <Datepicker v-model="datePicker" :placeholder="$t('date')"></Datepicker>
        </div>
        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="@/assets/icons/Number.svg"
            alt="user"
          />
          <v-select 
            :placeholder="$t('type')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
            :options="options0" :reduce="item => item.id" label="title" 
          />
        </div>

        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="@/assets/icons/allMoney.svg"
            alt="user"
          />
          <v-select 
            :placeholder="$t('color')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
            :options="colorOptions" :reduce="item => item.id" label="title" 
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
            :placeholder="$t('amount3')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
          />
        </div>

      </div>
    </template>
  </Modal>
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

        const datePicker = ref();
  
        const options0 = reactive([
            {
                id: 1,
                title: 'Поролон 1'
            },
            {
                id: 2,
                title: 'Поролон 2'
            },
        ])

      

        const colorOptions = reactive([
            {
                id: 1,
                title: 'Красный'
            },
            {
                id: 2,
                title: 'Жёлтый'
            },
            {
                id: 3,
                title: 'Синий'
            },
            {
                id: 4,
                title: 'Коричневый'
            },
            {
                id: 5,
                title: 'Чёрный'
            },
            {
                id: 6,
                title: 'Белый'
            },
        ])

      
        const toggleModal = () => {
            instance.parent.setupState.toggleModal()
            // isModalActive.value = !isModalActive.value;
        };



        onMounted(() => {

        });

        return {
          datePicker,
          options0,
          colorOptions,
          toggleModal,

        };
    }
}
</script>

<style>

</style>