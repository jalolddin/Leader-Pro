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
            :$t('processes')
        }}
      </h3>
      <span class="text-sm text-[#888A8F] mt-2">245 шт</span>
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
          {{$t('processes')}}
        </li>
      </ul>

      <button
        @click="toggleModal"
        class="mainBackgroundColor hover:scale-105 duration-300 text-white basicBtn"
      >
        <PlusIcon stroke="stroke-current mr-2" />
        Отправить сырьё
      </button>

      <!-- <button
        @click="toggleModal"
        :class="currantTable === 'table-4' ? 'opacity-0' : ''"
        class="mainBackgroundColor hover:scale-105 duration-300 text-white basicBtn"
      >
        <PlusIcon stroke="stroke-current mr-2" />
        Maxsulot qo'shish
      </button> -->
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
                <h3 class="a-table-title">{{$t('party_num')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('from_where')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('raw_party_num')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('amount')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('price_per_item')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('total_sum')}}</h3>
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
                <h3 class="a-table-text main-color-black">
                  1{{ item }}.06.2022
                </h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text main-color-black">Smala 412</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text">#1234</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text">China</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text">Бочка</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text green-color">{{ 99 * item }} {{$i18n.locale == 'ru' ? ' шт' : ' ta'}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text green-color">{{ 1200 * item }} {{$i18n.locale == 'ru' ? ' сум' : ' so`m'}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text green-color">{{ 1200 * 99 * item }} {{$i18n.locale == 'ru' ? ' сум' : ' so`m'}}</h3>
              </li>
              <li class="uk-width-expand">
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
            </ul>
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
                <h3 class="a-table-title">{{$t('amount')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title flex justify-center">{{$t('actions')}}</h3>
              </li>
            </ul>
          </div>

          <div class="a-table-body">
            <ul
              v-for="(item, index) in 3"
              class="uk-grid-collapse a-table-list border-t-[1.5px] borderBox"
              uk-grid :key="index"
            >
              <li class="uk-width-expand">
                <h3 class="a-table-text main-color-black">
                  1{{ item }}.06.2022
                </h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text main-color-black">Qattiq tosh 12m</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text warn-color">{{ 4 * item }} {{$i18n.locale == 'ru' ? ' шт' : ' ta'}}</h3>
              </li>
              <li class="uk-width-expand">
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
            </ul>
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
                          <li>
                            <h3 class="a-table-text">Ximiya DT</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">{{ item }}0,000 {{$i18n.locale == 'ru' ? ' шт' : ' ta'}}</h3>
                          </li>
                          <li class="w-[100px]">
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
                          <li>
                            <h3 class="a-table-text">Ximiya CV</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">{{ item }}0,000 {{$i18n.locale == 'ru' ? ' шт' : ' ta'}}</h3>
                          </li>
                          <li class="w-[100px]">
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
                        </ul>
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
                            <h3 class="a-table-title">{{$t('amount')}}</h3>
                          </li>
                          <li class="uk-width-expand">
                            <h3 class="a-table-title flex justify-center">{{$t('actions')}}</h3>
                          </li>
                        </ul>
                      </div>

                      <div class="a-card-body">
                        <ul
                          v-for="(item, index) in 2"
                          class="uk-grid-collapse uk-child-width-expand py-5 border-t-[1.5px] borderBox"
                          uk-grid :key="index"
                        >
                          <li>
                            <h3 class="a-table-text">Oq DDP suyuqlik</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">{{ item }}0,000 {{$i18n.locale == 'ru' ? ' шт' : ' ta'}}</h3>
                          </li>
                          <li class="w-[100px]">
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
                            <h3 class="a-table-title">{{$t('amount')}}</h3>
                          </li>
                          <li class="uk-width-expand">
                            <h3 class="a-table-title flex justify-center">{{$t('actions')}}</h3>
                          </li>
                        </ul>
                      </div>

                      <div class="a-card-body">
                        <ul
                          v-for="(item, index) in 2"
                          class="uk-grid-collapse uk-child-width-expand py-5 border-t-[1.5px] borderBox"
                          uk-grid :key="index"
                        >
                          <li>
                            <h3 class="a-table-text">Bisvol 22DT</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">{{ item }}0,000 {{$i18n.locale == 'ru' ? ' шт' : ' ta'}}</h3>
                          </li>
                          <li class="w-[100px]">
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
                        </ul>
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

    </div>
    <SendRawMaterials :isModalActive="isModalActive"/>
  </section>
</template>

<script>
import { ref } from "vue";
import PlusIcon from "@/assets/iconsVue/PlusIcon.vue";
import SmallArrowRight from "@/assets/iconsVue/SmallArrowRight.vue";
import Modal from '../../../components/base/Modal.vue'
import FunctionsIcon from "@/assets/iconsVue/FunctionsIcon.vue";
import SendRawMaterials from './components/SendRawMaterialsModal.vue'

export default {
  components: {
    Modal,
    SmallArrowRight,
    PlusIcon,
    FunctionsIcon,
    SendRawMaterials,
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

    const params = ref({
      page: 1,
    });


    const toggleModal = () => {
      isModalActive.value = !isModalActive.value
    }
    const togglePopup = (index) => {
      popUpActive.value[index] = !popUpActive.value[index];
    };

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

    const changeTable = (e) => {
      currantTable.value = e;
    };

    return {
      params,
      changeTable,
      currantTable,
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
