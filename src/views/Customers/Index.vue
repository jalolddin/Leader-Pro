<template>
  <section class="pb-20">
    <div class="pt-10 pb-8 wrapper client__header flex justify-between items-center border-b-[1.5px] borderBox">
      <div>
        <h3 class="sectionTitle">{{$t('list_of_clients')}}</h3>
        <!-- <span class="text-sm text-[#888A8F] mt-2">5ta mijoz mavjud</span> -->
        <span class="text-sm text-[#888A8F] mt-2">5 клиентов</span>
      </div>
      <router-link :to="{name: 'CustomersModal'}">
        <button
        @click="toggleModal()"
        class="mainBackgroundColor hover:scale-105 duration-300 text-white basicBtn"
        >
        <PlusIcon stroke="stroke-current mr-2" />
        {{$t('add')}}
      </button>
    </router-link>
    </div>

    <div class="a-table">
      <div class="table-1">
        <div class="wrapper border-b-[1.5px] borderBox">
          <!-- <div class="a-table-header">
            <ul class="uk-grid-collapse a-table-list" uk-grid>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('client_number')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('fullname')}}</h3>
              </li>
              <li class="uk-width-expand">
                 <h3 class="a-table-title">{{$t('fullname')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('debts')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('our_debt')}}</h3>
              </li>
              <li class="w-[100px]">
                <h3 class="a-table-title text-center">{{$t('functions')}}</h3>
              </li>
            </ul>
          </div> -->

          <div class="a-table-body">
            <ul
              v-for="(item, index) in 5"
              class="uk-grid-collapse a-table-list client border-t-[1.5px] borderBox"
              uk-grid
              :key="index"
            >
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('client_number')}}</h3>
                <h3 class="a-table-text main-color-black">00{{index + 1}}</h3>
              </li>
              <hr>
              <router-link tag="li" class="uk-width-expand" :to="{name: 'CustomersShow', params: {id: index}}">
                <h3 class="a-table-title">{{$t('fullname')}}</h3>
                <h3 class="a-table-text mainColorText">Jahongir Jumaev</h3>
              </router-link>
              <hr>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('phone_number')}}</h3>
                <h3 class="a-table-text main-color-black">
                  +99897555443{{ index }}
                </h3>
              </li>
              <hr>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('debts')}}</h3>
                <h3 class="a-table-text main-color-black">
                  {{ index + 1 }},000,000 {{$i18n.locale == 'ru' ? ' сум' : ' so`m'}}
                </h3>
              </li>
              <hr>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('our_debt')}}</h3>
                <h3 class="a-table-text">{{ index + 1 }}0,000,000 {{$i18n.locale == 'ru' ? ' сум' : ' so`m'}}</h3>
              </li>
              <hr>
              <li class="uk-width-expand">
                <h3 class="a-table-title text-center">{{$t('functions')}}</h3>
                <div class="relative">
                  <div
                    @click="togglePopup(index)"
                    class="cursor-pointer flex justify-center w-full"
                  >
                    <!-- ref="popUpRef" -->
                    <FunctionsIcon
                      stroke="stroke-[#5FC7D1] z-[-1]"
                      width="30"
                      height="30"
                    />
                  </div>

                  <functions-popup
                    v-if="popUpActive[index]"
                    :additonalClasses="'z-[11]'"
                  >
                    <template v-slot:FunctionsPopupContent>
                      <div class="flex flex-col space-y-3">
                        <button
                          class="text-[#E54D43] hover:scale-105 duration-300"
                        >
                          {{$t('delete')}}
                        </button>
                      </div>
                    </template>
                  </functions-popup>
                </div>
                <div
                  @click="togglePopup(index)"
                  v-if="popUpActive[index]"
                  class="w-[100vw] h-[100vh] z-[10] absolute top-1/2 -translate-y-1/2 right-0"
                ></div>
              </li>
              <br>
              <div class="line"></div>
            </ul>
          </div>
        </div>
      </div>
       <div class="flex justify-center mt-10">
        <v-pagination
          v-model="params.page"
          :pages="5"
          :range-size="1"
          @update:modelValue="updatePage"
          hideFirstButton="true"
          hideLastButton="true"
        />
      </div>
    </div>
  </section>
</template>

<script>
import { ref } from "vue";
import customersModal from './components/customersModal.vue'
import PlusIcon from "../../assets/iconsVue/PlusIcon.vue";
import FunctionsIcon from "../../assets/iconsVue/FunctionsIcon.vue";
import SmallArrowRight from "../../assets/iconsVue/SmallArrowRight.vue";


export default {
  components: {
    customersModal,
    SmallArrowRight,
    PlusIcon,
    FunctionsIcon,
  },
  setup() {
    let isModalActive = ref(false)
    let popUpActive = ref([false]);

    const togglePopup = (index) => {
      popUpActive.value[index] = !popUpActive.value[index];
    };

    const toggleModal = () => {
      isModalActive.value = !isModalActive.value
    }
    
     const params = ref({
      page: 1,
    });

    function updatePage(value) {
      console.log(value)
      if (currantTable === 'table-1') {
        // getSomeData(params)
      }
      if (currantTable === 'table-2') {
        // getAnotherData(params)
      }
      params.page = value;
    }

    return {
      popUpActive,
      togglePopup,
      params,
      updatePage,

      isModalActive,
      toggleModal,
    };
  },
};
</script>

<style></style>
