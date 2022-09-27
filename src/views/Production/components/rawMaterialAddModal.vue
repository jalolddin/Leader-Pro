<template>
   <Modal :isModalActive="isRawAddModalActive" @close="toggleModal">

    <template v-slot:modalHeader>
      <h3 class="text-lg font-medium text-center main-color-black">
        {{$t('raw_material_select')}}
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
          <v-select 
            :placeholder="$t('raw_material_type')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
            :options="options" :reduce="item => item.id" label="title" 
          />
        </div>
        <div class="relative flex">
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
            :placeholder="$t('amount')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
          />

          <v-select 
            :placeholder="$t('units')"
            class="ml-2 mt-1 w-full py-[14px] px-[10px] focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
            :options="TypeOptions" :reduce="item => item.id" label="title" 
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
        isRawAddModalActive: {
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

      
        const options = reactive([
            {
                id: 1,
                title: 'Химия 1'
            },
            {
                id: 2,
                title: 'Химия 2'
            },
        ])

        const TypeOptions = reactive([
            {
                id: 1,
                title: 'кг'
            },
            {
                id: 2,
                title: 'литр'
            },
        ])

      
        const toggleModal = () => {
          instance.parent.parent.parent.setupState.toggleRawAddModal()
        };
        onMounted(() => {
          
        });

        return {
          datePicker,
          options0,
          options,
          TypeOptions,
          toggleModal,
        };
    }
}
</script>

<style>

</style>