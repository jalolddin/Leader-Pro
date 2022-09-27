<template>
  <section class="pb-20">
    <div class="pt-10 pb-8 wrapper">
      <h3 class="sectionTitle">
       {{$t('permissions')}}
      </h3>
      <!-- <span class="text-sm text-[#888A8F] mt-2">5ta ruxsat mavjud</span> -->
      <span class="text-sm text-[#888A8F] mt-2">5 шт разрешений</span>
    </div>
    <div class="flex items-center justify-between border-y-[1.5px] borderBox wrapper h-[70px]">
      <div></div>
      <button class="mainBackgroundColor hover:scale-105 duration-300 text-white basicBtn">
        <img src="@/assets/icons/archive-add.svg" alt="" class="mr-2">
        {{$t('save')}}
      </button>
    </div>

    <div class="a-table flex">
      <div class="table-1 w-full border-r-[1.5px]">
        <div class="wrapper border-b-[1.5px] borderBox pb-10">
          <div class="a-table-header">
            <ul class="uk-grid-collapse a-table-list" uk-grid>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('name')}}</h3>
              </li>
              <li class="w-[100px]">
                <h3 class="a-table-title">{{$t('functions')}}</h3>
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
                <h3 class="a-table-text">Sotuv</h3>
              </li>
              <li class="w-[100px]">
                  <label class="relative cursor-pointer">
                    <input class="uk-checkbox absolute top-1 left-0" id="formcheck" type="checkbox">
                  </label>
              </li>
            </ul>
          </div>
        </div>
      </div>









      <div class="table-1 w-full border-r-[1.5px]">
        <div class="wrapper border-b-[1.5px] borderBox pb-10">
          <div class="a-table-header">
            <ul class="uk-grid-collapse a-table-list" uk-grid>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('name')}}</h3>
              </li>
              <li class="w-[100px]">
                <h3 class="a-table-title">{{$t('functions')}}</h3>
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
                <h3 class="a-table-text">Sotuv</h3>
              </li>
              <li class="w-[100px]">
                  <label class="relative cursor-pointer">
                    <input class="uk-checkbox absolute top-1 left-0" id="formcheck" type="checkbox">
                  </label>
              </li>
            </ul>
          </div>
        </div>
      </div>










      <div class="table-1 w-full">
        <div class="wrapper border-b-[1.5px] borderBox pb-10">
          <div class="a-table-header">
            <ul class="uk-grid-collapse a-table-list" uk-grid>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('name')}}</h3>
              </li>
              <li class="w-[100px]">
                <h3 class="a-table-title">{{$t('functions')}}</h3>
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
                <h3 class="a-table-text">Sotuv</h3>
              </li>
              <li class="w-[100px]">
                  <label class="relative cursor-pointer">
                    <input class="uk-checkbox absolute top-1 left-0" id="formcheck" type="checkbox">
                  </label>
              </li>
            </ul>
          </div>
        </div>
      </div>
    
       
    </div>
  </section>
</template>

<script>
import { ref } from "vue";
import PlusIcon from "../../assets/iconsVue/PlusIcon.vue";
import FunctionsIcon from "../../assets/iconsVue/FunctionsIcon.vue";
import SmallArrowRight from "../../assets/iconsVue/SmallArrowRight.vue";

export default {
  components: {
    SmallArrowRight,
    PlusIcon,
    FunctionsIcon,
  },
  setup() {
    let popUpActive = ref([false]);

    const togglePopup = (index) => {
      popUpActive.value[index] = !popUpActive.value[index];
    };

    return {
      popUpActive,
      togglePopup,
    };
  },
};
</script>

<style></style>
