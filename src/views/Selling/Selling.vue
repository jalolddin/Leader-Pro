<template>
  <section class="sailing-section pb-20">
    <div
      class="pt-10 pb-8 border-b-[1.5px] borderBox wrapper flex items-center justify-between"
    >
      <div class="sale__title">
        <h3 class="sectionTitle">{{$t('sales_history')}}</h3>
        <!-- <span class="text-sm text-[#888A8F] mt-2">914 ta sotuv</span> -->
        <span class="text-sm text-[#888A8F] mt-2">914 продаж</span>
      </div>
      <!-- <div class="flex items-center space-x-4">
        
         <div
          class="w-[170px] h-[60px] border-[1.5px] borderBox rounded-[12px] relative"
        >
          <div
            ref="typeDropdownRef"
            class="w-full h-full absolute left-0 top-0 cursor-pointer"
          ></div>
          <div class="flex main-color-black p-4 pr-6">
            <span class="mr-2">{{$t('type')}}:</span>
            <span class="w-full overflow-hidden font-semibold">{{
              currentType
            }}</span>
            <img
              :class="typeDropdownActive ? 'rotate-180' : ''"
              class="absolute right-4 top-1/2 -translate-y-1/2"
              src="../../assets/icons/smallArrowBottom.svg"
              alt="img"
            />
          </div>
          <ul
            :class="
              typeDropdownActive ? 'opacity-100 z-10 h-[134px]' : 'opacity-0 z-[-1] h-[0px]'
            "
            class="absolute left-1/2 -translate-x-1/2 top-[70px] mainBackgroundColorBlack w-[150px] scroll-none overflow-scroll p-4 rounded-[12px] text-white duration-300"
          >
            <li
              v-for="(item, index) in types"
              :key="index"
              @click="handleType(item)"
              class="py-1.5 cursor-pointer"
            >
              {{ item }}
            </li>
          </ul>
        </div>

        <div
          class="w-[150px] h-[60px] border-[1.5px] borderBox rounded-[12px] relative"
        >
          <div
            ref="monthDropdownRef"
            class="w-full h-full absolute left-0 top-0 cursor-pointer"
          ></div>
          <div class="flex main-color-black p-4 pr-6">
            <span class="mr-2">{{$t('month')}}:</span>
            <span class="w-full overflow-hidden font-semibold">{{
              currentMonth
            }}</span>
            <img
              :class="monthDropdownActive ? 'rotate-180' : ''"
              class="absolute right-4 top-1/2 -translate-y-1/2"
              src="../../assets/icons/smallArrowBottom.svg"
              alt="img"
            />
          </div>
          <ul
            :class="
              monthDropdownActive ? 'opacity-100 z-10 h-[134px]' : 'opacity-0 z-[-1] h-[0px]'
            "
            class="absolute left-1/2 -translate-x-1/2 top-[70px] mainBackgroundColorBlack w-[150px] scroll-none overflow-scroll p-4 rounded-[12px] text-white duration-300"
          >
            <li
              v-for="month in months"
              :key="month"
              @click="handleMonth(month)"
              class="py-1.5 cursor-pointer"
            >
              {{ month }}
            </li>
          </ul>
        </div>

      </div> -->
    </div>
    <div class="wrapper border-b-[1.5px] borderBox">
      <div class="a-table">
        <!-- <div class="a-table-header">
          <ul class="uk-grid-collapse a-table-list" uk-grid>
            <li class="uk-width-expand">
              <h3 class="a-table-title">{{$t('date')}}</h3>
            </li>
            <li class="uk-width-expand">
              <h3 class="a-table-title">{{$t('name')}}</h3>
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
              <h3 class="a-table-title">{{$t('advance_received')}}</h3>
            </li>
            <li class="uk-width-expand">
              <h3 class="a-table-title">{{$t('left_sum')}}</h3>
            </li>
          </ul>
        </div> -->
        <div class="a-table-body">
          <ul v-for="(item, index) in 7" :key="index" class="sale uk-grid-collapse a-table-list border-t-[1.5px] borderBox" uk-grid>
            <li class="uk-width-expand">
              <h3 class="a-table-title">{{$t('date')}}</h3>
              <h3 class="a-table-text main-color-black">1{{item}}.06.2022</h3>
            </li>
            <hr>
            <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('name')}}</h3>
              <h3 class="a-table-text main-color-black">Matras 1{{item + 1}} DP</h3>
            </li>
            <hr>
            <li class="uk-width-expand">
              <h3 class="a-table-title">{{$t('amount')}}</h3>
              <h3 class="a-table-text main-color-black">{{ item + 100 }} {{locale == 'ru' ? 'шт' : 'ta'}}</h3>
            </li>
            <hr>
            <li class="uk-width-expand">
              <h3 class="a-table-title">{{$t('price_per_item')}}</h3>
              <h3 class="a-table-text">{{item + 20}},000 uzs</h3>
            </li>
            <hr>
            <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('total_sum')}}</h3>
              <h3 class="a-table-text mainColorText">{{ item + 920 }},000 uzs</h3>
            </li>
            <hr>
            <li class="uk-width-expand">
              <h3 class="a-table-title">{{$t('advance_received')}}</h3>
              <h3 class="a-table-text green-color">{{ item + 4 }}00,000 uzs</h3>
            </li>
            <hr>
            <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('left_sum')}}</h3>
              <h3 class="a-table-text warn-color">{{ item + 5 }}10,000 uzs</h3>
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
  </section>
</template>

<script>
import SmallArrowRight from "../../assets/iconsVue/SmallArrowRight.vue";
import { ref, onMounted } from "vue";
import { useI18n } from 'vue-i18n'


export default {
  components: {
    SmallArrowRight,
    useI18n,
  },
  setup() {
    const {locale}  = useI18n()
    const months = ["iyul", "iyun", "avgust", "sentabr", "oktabr", "dekabr"];
    const types = ['Barchasi', '1 tasi'];
    let currentMonth = ref("Июль");
    let currentType = ref("Все");
    let monthDropdownActive = ref(false);
    let typeDropdownActive = ref(false);
    const monthDropdownRef = ref(null);
    const typeDropdownRef = ref(null)

    const handleMonth = (e) => {
      currentMonth.value = e;
    };

    const handleType = (e) => {
      currentType.value = e;
    };

    const openDropDown = (e) => {
      e.target === monthDropdownRef.value
        ? (monthDropdownActive.value = true)
        : (monthDropdownActive.value = false);

    e.target === typeDropdownRef.value
        ? (typeDropdownActive.value = true)
        : (typeDropdownActive.value = false);
    };

    onMounted(() => {
      window.addEventListener("click", openDropDown);
    });

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
      locale,
      months,
      types,
      handleMonth,
      handleType,
      currentMonth,
      currentType,
      openDropDown,
      monthDropdownActive,
      monthDropdownRef,
      typeDropdownActive,
      typeDropdownRef,
      params,
      updatePage
    };
  },
};
</script>

<style></style>
