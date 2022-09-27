<template>
  <section class="pb-20">
    <div class="pt-10 pb-10 wrapper border-b-[1.5px] borderBox">
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
      <span class="text-sm text-[#888A8F] mt-2">15 шт</span>
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
                <h3 class="a-table-title">{{$t('name')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('car_number')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('party_num')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('from_where')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('machine_party_num')}}</h3>
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
              v-for="(item, index) in 6"
              class="uk-grid-collapse a-table-list border-t-[1.5px] borderBox"
              uk-grid :key="index"
            >
              <li class="uk-width-expand">
                <h3 class="a-table-text main-color-black">
                  1{{ item }}.{{ item + 1 }}.2022
                </h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text main-color-black">Zil</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text">A{{item}}12CB</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text">#1234</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text">China</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text">Tara #4531</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text green-color">{{ 99 * item }} ta</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text green-color">{{ 30000 * item }} {{$i18n.locale == 'ru' ? ' сум' : ' so`m'}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text green-color">{{ 30000 * 99 * item }} {{$i18n.locale == 'ru' ? ' сум' : ' so`m'}}</h3>
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
import PlusIcon from "@/assets/iconsVue/PlusIcon.vue";
import SmallArrowRight from "@/assets/iconsVue/SmallArrowRight.vue";
import FunctionsIcon from "@/assets/iconsVue/FunctionsIcon.vue";

export default {
  components: {
    SmallArrowRight,
    PlusIcon,
    FunctionsIcon,
  },
  setup() {
    let currantTable = ref("table-1");
    let popUpActive = ref([false]);

    const changeTable = (e) => {
      currantTable.value = e;
    };

    const togglePopup = (index) => {
      popUpActive.value[index] = !popUpActive.value[index];
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

      popUpActive,
      togglePopup
    };
  },
};
</script>

<style></style>
