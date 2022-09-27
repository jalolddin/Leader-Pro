<template>
   <Modal :isModalActive="isModalActive" @close="toggleModal" :width="modalWidth">
    <template v-slot:modalHeader>
      <h3 class="text-lg font-medium text-center main-color-black">
        {{$t('there_was_sale')}}
      </h3>
    </template>

    <template v-slot:modalBody>
      <div class="mt-4 space-y-3">
        <div class="flex">
          <div class="relative mt-1 w-1/2 py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg flex justify-between">
            <img
              class="absolute left-4 top-1/2 -translate-y-1/2"
              src="@/assets/icons/allMoney.svg"
              alt="user"
            />
            <span>{{$t('export')}}</span>
            <input type="radio" value="1" name="soldType" v-model="soldType" class="w-4">
          </div>
          <div class="relative ml-2 mt-1 w-1/2 py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg flex justify-between">
            <img
              class="absolute left-4 top-1/2 -translate-y-1/2"
              src="@/assets/icons/allMoney.svg"
              alt="user"
            />
            <span>{{$t('local')}}</span>
            <input type="radio" value="2" name="soldType" v-model="soldType" class="w-4">
          </div>
        </div>
        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="@/assets/icons/allMoney.svg"
            alt="user"
          />
          <Datepicker v-model="dateTime" :placeholder="$t('date')"></Datepicker>
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
            :placeholder="$t('client_number')"
            v-model="clientNum"
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
            :placeholder="$t('client_name')"
            v-model="clientName"
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
            :placeholder="$t('client_phone_number')"
            v-model="clientPhone"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
          />
        </div>
        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="../../assets/icons/Number.svg"
            alt="user"
          />
          <select v-model="productType"
             class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg">
            <option :value="item.id" v-for="(item, index) in options" :key="index" :selected="index == 0 ? item.id : ''">{{item.title}}</option>
          </select>
          <!-- <v-select 
            :placeholder="$t('product_category')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
            :options="options" :reduce="item => item.id" label="title" 
            v-model="productType"
          /> -->
        </div>




        <div v-if="productType == 1 || productType == 2">
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
              :placeholder="$t('length')"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              :placeholder="$t('width')"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              :placeholder="$t('thickness')"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              :placeholder="$t('number')"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              :placeholder="$t('cube')"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              :placeholder="$t('amount_given')"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
            />
          </div>
        </div>




        <div v-if="productType == 3">
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
              :placeholder="$t('number2')"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              v-model="amount"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              v-model="unitSum"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              v-model="totalSum"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              :placeholder="$t('amount_given')"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
            />
          </div>
        </div>






        <div v-if="productType == 4">
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
              :placeholder="$t('number2')"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              v-model="amount"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              v-model="unitSum"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              v-model="totalSum"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              :placeholder="$t('amount_given')"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
            />
          </div>
        </div>









        <div v-if="productType == 5">
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
              :placeholder="$t('number2')"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              v-model="amount"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              v-model="unitSum"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              v-model="totalSum"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              :placeholder="$t('amount_given')"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
            />
          </div>
        </div>











        <div v-if="productType == 6">
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
              :placeholder="$t('number2')"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              v-model="amount"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              v-model="unitSum"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              v-model="totalSum"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
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
              :placeholder="$t('amount_given')"
              class="my-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
            />
          </div>
        </div>






        







      </div>
    </template>
  </Modal>
</template>

<script>
import { getCurrentInstance } from "vue";
import { ref, onMounted, reactive, watch } from "vue";
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
        },
        modalWidth: {
            type: [Number, String],
            required: false,
        },
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





        //================= VARIABLES START =================
        let today = new Date()
        const dateTime = ref(today);
        const clientNum = ref();
        const clientName = ref();
        const clientPhone = ref();


        const amount = ref();
        const unitSum = ref();
        const totalSum = ref();

        const soldType = ref(2);
        const productType = ref(1);
        //================= VARIABLES END =================



        watch(clientNum, (newValue, prevValue) => {
          if(newValue == '101'){
            clientName.value = "Dilmurod"
            clientPhone.value = "+998995552244"
          }
        })


        watch(amount, (newValue, prevValue) => {
          if(newValue){
            totalSum.value = amount.value * unitSum.value
          }
        })
        watch(unitSum, (newValue, prevValue) => {
          if(newValue){
            totalSum.value = amount.value * unitSum.value
          }
        })




        const options = reactive([
            {
                id: 1,
                title: 'Porolon kub'
            },
            {
                id: 2,
                title: 'Porolon kg'
            },
            {
                id: 3,
                title: 'Gubka'
            },
            {
                id: 4,
                title: 'Yostiq'
            },
            {
                id: 5,
                title: 'Matras'
            },
            {
                id: 6,
                title: 'Bochka'
            },
            {
                id: 6,
                title: 'Boshqa mahsulotlar'
            },
        ])
      
        const toggleModal = () => {
            instance.parent.setupState.toggleSoldModal()
        };
        onMounted(() => {

        });

        return {
            options,

            clientNum,
            clientName,
            clientPhone,

            amount,
            unitSum,
            totalSum,

            dateTime,
            soldType,
            productType,


            toggleModal,
        };
    }
}
</script>

<style>

</style>