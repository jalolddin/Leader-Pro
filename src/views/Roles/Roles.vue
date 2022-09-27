<template>
  <section class="pb-20">
    <div class="pt-10 pb-8 wrapper">
      <h3 class="sectionTitle">
       {{$t('roles')}}
      </h3>
      <span class="text-sm text-[#888A8F] mt-2">5 ролей</span>
    </div>
    <div class="flex items-center justify-between border-y-[1.5px] borderBox wrapper h-[70px]">
      <div></div>
      <button class="mainBackgroundColor hover:scale-105 duration-300 text-white basicBtn">
        <PlusIcon stroke="stroke-current mr-2" />
        {{$t('add')}}
      </button>
    </div>

    <div class="a-table">
      <div class="table-1">
        <div class="wrapper border-b-[1.5px] borderBox pb-10">
          <div class="a-table-header">
            <ul class="uk-grid-collapse a-table-list" uk-grid>
              <li class="uk-width-expand">
                <h3 class="a-table-title">{{$t('date')}}</h3>
              </li>
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
              v-for="(item, index) in 5"
              class="uk-grid-collapse a-table-list border-t-[1.5px] borderBox"
              uk-grid :key="index"
            >
              <li class="uk-width-expand">
                <h3 class="a-table-text main-color-black">12.06.2022</h3>
              </li>
              <li class="uk-width-expand">
                <h3 class="a-table-text">Admin</h3>
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

                  <functions-popup v-if="popUpActive[index]" :additonalClasses="'z-[11]'">
                    <template v-slot:FunctionsPopupContent>
                      <div class="flex flex-col space-y-3">
                        <button
                          class="mainColorText hover:scale-105 duration-300"
                        >
                          {{$t('freeze')}}
                        </button>
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
