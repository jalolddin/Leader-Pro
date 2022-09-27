<template>
  <section class="pb-20">
    <div class="pt-10 pb-8 wrapper">
      <h3 class="sectionTitle">
        {{
          currantTable === "table-1"
            ?$t('comes_history')
            : currantTable === "table-2"
            ?$t('lefts_history')
            : currantTable === "table-3"
            ?$t('warehouse')
            :$t('ready_products')
        }}
      </h3>
      <!-- <span class="text-sm text-[#888A8F] mt-2">245 ta kirim chiqim tarixi</span> -->
      <span class="text-sm text-[#888A8F] mt-2">245 шт приходов и расходов</span>
    </div>
    <div
      class="flex items-center justify-between border-y-[1.5px] borderBox wrapper h-[70px]"
    >
      <ul class="basicTab">
        <li
          @click="changeTable('table-1')"
          class="mainColor font-medium duration-300"
          :class="currantTable === 'table-1' ? 'active' : ''"
        >
          {{$t('come')}}
        </li>
        <li
          @click="changeTable('table-2')"
          class="mainColor font-medium duration-300"
          :class="currantTable === 'table-2' ? 'active' : ''"
        >
          {{$t('left')}}
        </li>
        <li
          @click="changeTable('table-3')"
          class="mainColor font-medium duration-300"
          :class="currantTable === 'table-3' ? 'active' : ''"
        >
          {{$t('warehouse')}}
        </li>
        <li
          @click="changeTable('table-4')"
          class="mainColor font-medium duration-300"
          :class="currantTable === 'table-4' ? 'active' : ''"
        >
          {{$t('ready_products')}}
        </li>
      </ul>

      <button
        @click="toggleModal()"
        :class="currantTable === 'table-4' ? 'opacity-0' : ''"
        class="mainBackgroundColor hover:scale-105 duration-300 text-white basicBtn"
      >
        <PlusIcon stroke="stroke-current mr-2" />
        {{$t('production')}}
      </button>
    </div>

    <div class="a-table">
      <div class="table-1" v-if="currantTable === 'table-1'">
        <div class="wrapper border-b-[1.5px] borderBox">
          <div class="a-table-header">
            <ul class="uk-grid-collapse a-table-list" uk-grid>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('date')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('type')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('name')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('amount')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('expenses')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title flex justify-center">{{$t('actions')}}</h3>
              </li>
            </ul>
          </div>

          <div class="a-table-body">
            <ul
              v-for="(item, index) in 10"
              class="uk-grid-collapse a-table-list border-t-[1.5px] borderBox"
              uk-grid :key="index"
            > 
              <li class="uk-width-expand">
                <h3 class="a-table-text main-color-black">12.06.2022</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text main-color-black">Yostiq</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text">Kley mantana</h3>
              </li>
              <li class="uk-width-expand">
                <h3
                  class="a-table-text green-color"
                >
                  {{ 990 + item }} ta
                </h3>
              </li>
              <li class="uk-width-expand">
                <div class="inline-block relative group">
                  <h3 class="a-table-text mainColorText">{{$t('show')}}</h3>
                  <div
                    class="hidden group-hover:block duration-300 z-[2] absolute left-1/2 top-1/2 h-auto -translate-x-1/2 mainBackgroundColorBlack w-[150px] p-4 rounded-[12px]"
                  >
                    <div class="relative w-full">
                      <span class="text-[12px] text-[#888A8F]">{{$t('foam')}}</span>
                      <p class="text-white text-sm font-semibold">
                        10 ta
                      </p>
                      <span class="text-[12px] text-[#888A8F]">Material</span>
                      <p class="text-white text-sm font-semibold">
                        20 metr
                      </p>
                      <span class="text-[12px] text-[#888A8F]">Kant</span>
                      <p class="text-white text-sm font-semibold">
                        10 metr
                      </p>
                      <span class="text-[12px] text-[#888A8F]">Ip</span>
                      <p class="text-white text-sm font-semibold">
                        2 ta
                      </p>
                      <span class="text-[12px] text-[#888A8F]">Tugma</span>
                      <p class="text-white text-sm font-semibold">
                        6 ta
                      </p>
                      <span class="text-[12px] text-[#888A8F]">Salafan</span>
                      <p class="text-white text-sm font-semibold">
                        2 ta
                      </p>
                      <span class="text-[12px] text-[#888A8F]">Skotch</span>
                      <p class="text-white text-sm font-semibold">
                        0.5 ta
                      </p>
                      <span class="text-[12px] text-[#888A8F]">Zamok</span>
                      <p class="text-white text-sm font-semibold">
                        2 ta
                      </p>
                    </div>
                  </div>
                </div>
              </li>
              <li class="uk-width-expand relative">
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
                        class="text-[#eac544] hover:scale-105 duration-300"
                      >
                        {{$t('edit')}}
                      </button>
                      <button
                        class="text-[#E54D43] hover:scale-105 duration-300"
                      >
                        {{$t('delete')}}
                      </button>
                    </div>
                  </template>
                </functions-popup>
              </li>
            </ul>
          </div>
        </div>
      </div>

      <div class="table-2" v-if="currantTable === 'table-2'">
        <div class="wrapper border-b-[1.5px] borderBox">
          <div class="a-table-header">
            <ul class="uk-grid-collapse a-table-list" uk-grid>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('date')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('type')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('name')}}</h3>
              </li>
              <li class="w-[100px]">
                <h3 class="a-table-title">{{$t('amount')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title flex justify-center">{{$t('actions')}}</h3>
              </li>
            </ul>
          </div>

          <div class="a-table-body">
            <ul
              v-for="(item, index) in 10"
              class="uk-grid-collapse a-table-list border-t-[1.5px] borderBox"
              uk-grid :key="index"
            >
              <li class="uk-width-expand">
                <h3 class="a-table-text main-color-black">12.06.2022</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text main-color-black">Yostiq</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text">Kley mantana</h3>
              </li>
              <li class="w-[100px]">
                <h3
                  class="a-table-text warn-color"
                >
                  {{ 990 + item }} ta
                </h3>
              </li>
              <li class="uk-width-expand relative">
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
                        class="text-[#eac544] hover:scale-105 duration-300"
                      >
                        {{$t('edit')}}
                      </button>
                      <button
                        class="text-[#E54D43] hover:scale-105 duration-300"
                      >
                        {{$t('delete')}}
                      </button>
                    </div>
                  </template>
                </functions-popup>
              </li>
            </ul>
          </div>
        </div>
      </div>

     <div class="table-3 pt-5" v-if="currantTable === 'table-3'">
        <div class="wrapper border-b-[1.5px] borderBox">
          <div
            class="uk-grid-medium uk-grid-match uk-child-width-expand"
            uk-grid
          >
            <div>
              <div class="a-card">
                <div class="uk-grid-collapse uk-child-width-1-2" uk-grid>
                  <div>
                    <div class="border-r-[1.5px] borderBox pr-10">
                      <div class="a-card-header">
                        <ul
                          class="uk-grid-collapse uk-child-width-expand pb-5"
                          uk-grid
                        >
                          <li class="uk-width-expand">
                            <h3 class="a-table-title">{{$t('type')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('name')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('amount')}}</h3>
                          </li>
                          <li class="uk-width-expand">
                            <h3 class="a-table-title flex justify-center">{{$t('actions')}}</h3>
                          </li>
                        </ul>
                      </div>

                      <div class="a-card-body">
                        <ul
                          v-for="(item, index) in 5"
                          class="uk-grid-collapse uk-child-width-expand py-5 border-t-[1.5px] borderBox"
                          uk-grid :key="index"
                        >
                          <li class="uk-width-expand">
                            <h3 class="a-table-text main-color-black">Yostiq</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">Porolom 1{{item}} talik</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">{{item + 1}}1,900 kg</h3>
                          </li>
                          <li class="uk-width-expand relative">
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
                                    class="text-[#eac544] hover:scale-105 duration-300"
                                  >
                                    {{$t('edit')}}
                                  </button>
                                  <button
                                    class="text-[#E54D43] hover:scale-105 duration-300"
                                  >
                                    {{$t('delete')}}
                                  </button>
                                </div>
                              </template>
                            </functions-popup>
                          </li>
                        </ul>
                      </div>
                    </div>
                  </div>
                  <div>
                    <div class="pl-10">
                      <div class="a-card-header">
                        <ul
                          class="uk-grid-collapse uk-child-width-expand pb-5"
                          uk-grid
                        >
                          <li class="uk-width-expand">
                            <h3 class="a-table-title">{{$t('type')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('name')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('amount')}}</h3>
                          </li>
                          <li class="uk-width-expand">
                            <h3 class="a-table-title flex justify-center">{{$t('actions')}}</h3>
                          </li>
                        </ul>
                      </div>

                      <div class="a-card-body">
                        <ul
                          v-for="(item, index) in 5"
                          class="uk-grid-collapse uk-child-width-expand py-5 border-t-[1.5px] borderBox"
                          uk-grid :key="index"
                        >
                          <li class="uk-width-expand">
                            <h3 class="a-table-text main-color-black">Yostiq</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">Porolom {{ item * 10 }} talik</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">{{item + 1}}0,420 kgl</h3>
                          </li>
                          <li class="uk-width-expand relative">
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
                                    class="text-[#eac544] hover:scale-105 duration-300"
                                  >
                                    {{$t('edit')}}
                                  </button>
                                  <button
                                    class="text-[#E54D43] hover:scale-105 duration-300"
                                  >
                                    {{$t('delete')}}
                                  </button>
                                </div>
                              </template>
                            </functions-popup>
                          </li>
                        </ul>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

       <div class="table-4 pt-5" v-if="currantTable === 'table-4'">
        <div class="wrapper border-b-[1.5px] borderBox">
          <div
            class="uk-grid-medium uk-grid-match uk-child-width-expand"
            uk-grid
          >
            <div>
              <div class="a-card">
                <div class="uk-grid-collapse uk-child-width-1-2" uk-grid>
                  <div>
                    <div class="border-r-[1.5px] borderBox pr-10">
                      <div class="a-card-header">
                        <ul
                          class="uk-grid-collapse uk-child-width-expand pb-5"
                          uk-grid
                        >
                          <li class="uk-width-expand">
                            <h3 class="a-table-title">{{$t('type')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('name')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('amount')}}</h3>
                          </li>
                           <li class="uk-width-expand">
                            <h3 class="a-table-title flex justify-center">{{$t('actions')}}</h3>
                          </li>
                        </ul>
                      </div>

                      <div class="a-card-body">
                        <ul
                          v-for="(item, index) in 10"
                          class="uk-grid-collapse uk-child-width-expand py-5 border-t-[1.5px] borderBox"
                          uk-grid :key="index"
                        >
                          <li class="uk-width-expand">
                            <h3 class="a-table-text main-color-black">Yostiq</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">Yostiq yumshoq 1{{item}} DP</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">{{item}},605 ta</h3>
                          </li>
                          <li class="uk-width-expand relative">
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
                                    class="text-[#eac544] hover:scale-105 duration-300"
                                  >
                                    {{$t('edit')}}
                                  </button>
                                  <button
                                    class="text-[#E54D43] hover:scale-105 duration-300"
                                  >
                                    {{$t('delete')}}
                                  </button>
                                </div>
                              </template>
                            </functions-popup>
                          </li>
                        </ul>
                      </div>
                    </div>
                  </div>
                  <div>
                    <div class="pl-10">
                      <div class="a-card-header">
                        <ul
                          class="uk-grid-collapse uk-child-width-expand pb-5"
                          uk-grid
                        >
                          <li class="uk-width-expand">
                            <h3 class="a-table-title">{{$t('type')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('name')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('amount')}}</h3>
                          </li>
                           <li class="uk-width-expand">
                            <h3 class="a-table-title flex justify-center">{{$t('actions')}}</h3>
                          </li>
                        </ul>
                      </div>

                      <div class="a-card-body">
                        <ul
                          v-for="(item, index) in 10"
                          class="uk-grid-collapse uk-child-width-expand py-5 border-t-[1.5px] borderBox"
                          uk-grid :key="index"
                        >
                          <li class="uk-width-expand">
                            <h3 class="a-table-text main-color-black">Yostiq</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">Ortopedik yostiq {{item * 20}} QL</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">{{item * 40}},0 ta</h3>
                          </li>
                          <li class="uk-width-expand relative">
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
                                    class="text-[#eac544] hover:scale-105 duration-300"
                                  >
                                    {{$t('edit')}}
                                  </button>
                                  <button
                                    class="text-[#E54D43] hover:scale-105 duration-300"
                                  >
                                    {{$t('delete')}}
                                  </button>
                                </div>
                              </template>
                            </functions-popup>
                          </li>
                        </ul>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
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
    <pillowModal :isModalActive="isModalActive"/>
  </section>
</template>

<script>
import { ref } from "vue";
import pillowModal from './components/pillowModal.vue'
import PlusIcon from "@/assets/iconsVue/PlusIcon.vue";
import SmallArrowRight from "@/assets/iconsVue/SmallArrowRight.vue";
import FunctionsIcon from "@/assets/iconsVue/FunctionsIcon.vue";

export default {
  components: {
    pillowModal,
    SmallArrowRight,
    PlusIcon,
    FunctionsIcon,
  },
  setup() {
    let currantTable = ref("table-1");
    let isModalActive = ref(false)

    let popUpActive0 = ref([false]);
    let popUpActive1 = ref([false]);
    let popUpActive2 = ref([false]);
    let popUpActive3 = ref([false]);
    let popUpActive4 = ref([false]);
    let popUpActive = ref([false]);

    const toggleModal = () => {
      isModalActive.value = !isModalActive.value
    }

    const togglePopup = (index) => {
      popUpActive.value[index] = !popUpActive.value[index];
    };


    const changeTable = (e) => {
      currantTable.value = e;
    };

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
      changeTable,
      currantTable,
      params,
      updatePage,
      isModalActive,
      toggleModal,


      popUpActive0,
      popUpActive1,
      popUpActive2,
      popUpActive3,
      popUpActive4,
      popUpActive,
      togglePopup
    };
  },
};
</script>

<style></style>
