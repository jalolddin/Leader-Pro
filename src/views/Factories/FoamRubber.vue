<template>
  <section class="pb-20">
    <div class="pt-10 pb-8 wrapper">
      <h3 class="sectionTitle">
        {{
          currantTable === "table-1"
            ? "Kirim tarixi"
            : currantTable === "table-2"
            ? "Chiqimlar tarixi"
            : currantTable === "table-3"
            ? "Mavjud xomashyolar"
            : "Tayyor mahsulotlar"
        }}
      </h3>
      <span class="text-sm text-[#888A8F] mt-2"
        >245 ta kirim chiqim tarixi</span
      >
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
        :class="currantTable === 'table-4' ? 'opacity-0' : ''"
        class="mainBackgroundColor hover:scale-105 duration-300 text-white basicBtn"
      >
        <PlusIcon stroke="stroke-current mr-2" />
        {{$t('add_product')}}
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
              <li class="w-[100px]">
                <h3 class="a-table-title">{{$t('amount')}}</h3>
              </li>
            </ul>
          </div>

          <div class="a-table-body">
            <ul
              v-for="(item, index) in 10"
              class="uk-grid-collapse a-table-list border-t-[1.5px] borderBox"
              uk-grid
            >
              <li class="uk-width-expand">
                <h3 class="a-table-text main-color-black">1{{item}}.06.2022</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text main-color-black">{{$t('raw')}}</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text">Figurnaya rezka {{item + 1}}0 DD</h3>
              </li>
              <li class="w-[100px]">
                <h3
                  class="a-table-text green-color"
                >
                  {{ 70 + item }} ta
                </h3>
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
            </ul>
          </div>

          <div class="a-table-body">
            <ul
              v-for="(item, index) in 10"
              class="uk-grid-collapse a-table-list border-t-[1.5px] borderBox"
              uk-grid
            >
              <li class="uk-width-expand">
                <h3 class="a-table-text main-color-black">12.06.2022</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text main-color-black">Figurnaya rezka</h3>
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
                          <li>
                            <h3 class="a-table-title">{{$t('name')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('amount')}}</h3>
                          </li>
                        </ul>
                      </div>

                      <div class="a-card-body">
                        <ul
                          v-for="(item, index) in 5"
                          class="uk-grid-collapse uk-child-width-expand py-5 border-t-[1.5px] borderBox"
                          uk-grid
                        >
                          <li>
                            <h3 class="a-table-text">Porolom 1{{item}} talik</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">{{item + 1}} ta</h3>
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
                          <li>
                            <h3 class="a-table-title">{{$t('name')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('amount')}}</h3>
                          </li>
                        </ul>
                      </div>

                      <div class="a-card-body">
                        <ul
                          v-for="(item, index) in 5"
                          class="uk-grid-collapse uk-child-width-expand py-5 border-t-[1.5px] borderBox"
                          uk-grid
                        >
                          <li>
                            <h3 class="a-table-text">Figurnaya rezka 1{{item + 1}} DP</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">{{item * 3}},0 ta</h3>
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
                          <li>
                            <h3 class="a-table-title">{{$t('name')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('amount')}}</h3>
                          </li>
                        </ul>
                      </div>

                      <div class="a-card-body">
                        <ul
                          v-for="(item, index) in 5"
                          class="uk-grid-collapse uk-child-width-expand py-5 border-t-[1.5px] borderBox"
                          uk-grid
                        >
                          <li>
                            <h3 class="a-table-text">Figurnaya rezka 1{{item}} DP</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">{{item + 222}} ta</h3>
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
                          <li>
                            <h3 class="a-table-title">{{$t('name')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('amount')}}</h3>
                          </li>
                        </ul>
                      </div>

                      <div class="a-card-body">
                        <ul
                          v-for="(item, index) in 5"
                          class="uk-grid-collapse uk-child-width-expand py-5 border-t-[1.5px] borderBox"
                          uk-grid
                        >
                          <li>
                            <h3 class="a-table-text">Figurnaya rezka {{item}}9 DP</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">{{item * 30}},0 ta</h3>
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
  </section>
</template>

<script>
import { ref } from "vue";
import PlusIcon from "@/assets/iconsVue/PlusIcon.vue";
import SmallArrowRight from "@/assets/iconsVue/SmallArrowRight.vue";
export default {
  components: {
    SmallArrowRight,
    PlusIcon,
  },
  setup() {
    let currantTable = ref("table-1");

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
      updatePage
    };
  },
};
</script>

<style></style>
