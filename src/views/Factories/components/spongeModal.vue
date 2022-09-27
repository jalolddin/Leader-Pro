<template>
   <Modal :isModalActive="isModalActive" @close="toggleModal">

    <template v-slot:modalHeader>
      <h3 class="text-lg font-medium text-center main-color-black">
        {{$t('sponge_production')}}
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
          <Datepicker v-model="date" :placeholder="$t('date')"></Datepicker>
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
            :options="options" :reduce="item => item.id" label="title" 
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
            :placeholder="$t('name')"
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
            :placeholder="$t('amount')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
          />
        </div>

        <hr class="">

        <div class="flex">
           <div class="relative w-8/12">
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
                :placeholder="$t('foam')"
                class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
              />
            </div>
            <div class="relative w-4/12">
              <input
                type="text"
                name="text"
                autocomplete="off"
                required
                :placeholder="$t('amount2')"
                class="mt-1 w-full py-[14px] px-[24px] ml-[5px] focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
              />
            </div>
        </div>





        <div class="flex">
           <div class="relative w-8/12">
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
                :placeholder="$t('fabric')"
                class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
              />
            </div>
            <div class="relative w-4/12">
              <input
                type="text"
                name="text"
                autocomplete="off"
                required
                :placeholder="$t('amount2')"
                class="mt-1 w-full py-[14px] px-[24px] ml-[5px] focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
              />
            </div>
        </div>











        <div class="flex">
           <div class="relative w-8/12">
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
                :placeholder="$t('salafan')"
                class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
              />
            </div>
            <div class="relative w-4/12">
              <input
                type="text"
                name="text"
                autocomplete="off"
                required
                :placeholder="$t('amount2')"
                class="mt-1 w-full py-[14px] px-[24px] ml-[5px] focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
              />
            </div>
        </div>






        <div class="flex">
           <div class="relative w-8/12">
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
                :placeholder="$t('adhesive_tape')"
                class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
              />
            </div>
            <div class="relative w-4/12">
              <input
                type="text"
                name="text"
                autocomplete="off"
                required
                :placeholder="$t('amount2')"
                class="mt-1 w-full py-[14px] px-[24px] ml-[5px] focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
              />
            </div>
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
        console.log(instance.parent);
        const router = useRouter();
        const route = useRoute();
        const { t } = useI18n()


        const options = reactive([
            {
                id: 1,
                title: 'mahsulot 1'
            },
            {
                id: 2,
                title: 'mahsulot 2'
            },
        ])
      
        const toggleModal = () => {
            instance.parent.setupState.toggleModal()
            // isModalActive.value = !isModalActive.value;
        };
        onMounted(() => {

        });

        return {
            options,
            toggleModal,
        };
    }
}
</script>

<style>

</style>