<template>
   <Modal :isModalActive="isModalActive" @close="toggleModal">
    <template v-slot:modalHeader>
      <h3 class="text-lg font-medium text-center main-color-black">
        {{$t('raw_material_arrived')}}
      </h3>
    </template>

    <template v-slot:modalBody>
      <div class="mt-4 space-y-3">
        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="../../assets/icons/allMoney.svg"
            alt="user"
          />
          <Datepicker v-model="dateTime" :placeholder="$t('date')"></Datepicker>
          <!-- <input
            type="text"
            name="text"
            autocomplete="off"
            required
            :placeholder="$t('date')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
          /> -->
        </div>
        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="../../assets/icons/Number.svg"
            alt="user"
          />
          <v-select 
            :placeholder="$t('product_category')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
            :options="rawMaterialOptions" :reduce="item => item.id" label="title" 
          />
        </div>
        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="../../assets/icons/Number.svg"
            alt="user"
          />
          <v-select 
            :placeholder="$t('raw_material_type')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
            :options="options" :reduce="item => item.id" label="title" 
          />
        </div>
        <!-- <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="../../assets/icons/Number.svg"
            alt="user"
          />
          <input
            type="text"
            name="text"
            autocomplete="off"
            required
            :placeholder="$t('name')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
          />
        </div> -->
        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="../../assets/icons/allMoney.svg"
            alt="user"
          />
          <v-select 
            :placeholder="$t('raw_party_num')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
            :options="rawPartyNumOptions" :reduce="item => item.id" label="title" 
          />
        </div>
        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="../../assets/icons/allMoney.svg"
            alt="user"
          />
          <input
            type="text"
            name="text"
            autocomplete="off"
            required
            :placeholder="$t('party_num')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
          />
        </div>
        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="../../assets/icons/allMoney.svg"
            alt="user"
          />
          <input
            type="text"
            name="text"
            autocomplete="off"
            required
            :placeholder="$t('from_where')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
          />
        </div>
        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="../../assets/icons/allMoney.svg"
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
        </div>
        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="../../assets/icons/allMoney.svg"
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
            src="../../assets/icons/allMoney.svg"
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
        
        <!-- <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="../../assets/icons/allMoney.svg"
            alt="user"
          />
          <input
            type="text"
            name="text"
            autocomplete="off"
            required
            :placeholder="$t('amount_given')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
          />
        </div> -->



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
import { useI18n } from 'vue-i18n'

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
        const { t } = useI18n()

        let today = new Date()
        const dateTime = ref(today);

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
        
        const rawPartyNumOptions = reactive([
            {
                id: 1,
                title: 'Тара 1'
            },
            {
                id: 2,
                title: 'Тара 2'
            },
        ])

        
        const rawMaterialOptions = reactive([
            {
                id: 1,
                title: 'Сырье'
            },
            {
                id: 2,
                title: 'Аксессуар'
            },
            {
                id: 3,
                title: 'Оборудование'
            },
            {
                id: 4,
                title: 'Техника'
            },
        ])
      
        const toggleModal = () => {
            instance.parent.setupState.toggleModal()
        };
        onMounted(() => {

        });

        return {
            options,
            rawPartyNumOptions,
            rawMaterialOptions,
            dateTime,

            toggleModal,
        };
    }
}
</script>

<style>

</style>