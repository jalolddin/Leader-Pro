<template>
  <section class="admins-section">
    <div class="pt-10">
      <div class="wrapper">
        <h3 class="sectionTitle">{{ currantTable === 'table-1' ? $t('employees_list') : '' }}</h3>
        <span class="text-sm text-[#888A8F] mt-2">{{ currantTable === 'table-1' ? ('72 ' + (locale == 'ru' ? ' ' : 'ta ') + $t('employee')) : '6 ta admin' }}</span>
      </div>
      <div
        class="mt-10 flex items-center justify-between border-y-[1.5px] borderBox wrapper h-[70px]"
      >
        <ul class="basicTab">
          <li
            @click="changeTable('table-1')"
            class="mainColor font-medium"
            :class="currantTable === 'table-1' ? 'active' : ''"
          >
            {{$t('employees')}}
          </li>
          <!-- <li
            @click="changeTable('table-2')"
            class="mainColor font-medium"
            :class="currantTable === 'table-2' ? 'active' : ''"
          >
            Adminlar
          </li> -->
        </ul>

        <button
          @click="toggleModal()"
          :class="currantTable === 'table-2' ? 'opacity-1' : 'opacity-0'"
          class="mainBackgroundColor hover:scale-105 duration-300 text-white basicBtn"
        >
          <PlusIcon stroke="stroke-current mr-2" />
          Yangi admin qo‘shish
        </button>
      </div>
    </div>

    <div class="wrapper border-b-[1.5px] borderBox">
      <div class="table">
        <div class="table__header">
          <div v-if="currantTable == 'table-1'" class="table-1">
            <ul>
              <li>
                <h3>{{$t('fullname')}}</h3>
              </li>
              <li>
                <h3>{{$t('department')}}</h3>
              </li>
              <li>
                <h3>{{$t('job')}}</h3>
              </li>
              <li>
                <h3>{{$t('salary')}}</h3>
              </li>
              <li>
                <h3>{{$t('salary_for_current_month')}}</h3>
              </li>
              <li>
                <h3>{{$t('employment_date')}}</h3>
              </li>
              <li>
                <h3 class="a-table-title flex justify-center">{{$t('actions')}}</h3>
              </li>
            </ul>
          </div>
          <div v-if="currantTable == 'table-2'" class="table-2">
            <ul>
              <li>
                <h3>Ismi</h3>
              </li>
              <li>
                <h3>Admin lavozimi</h3>
              </li>
              <li>
                <h3>Admin lavozimi</h3>
              </li>
              <li>
                <h3 class="text-center">{{$t('functions')}}</h3>
              </li>
            </ul>
          </div>
        </div>

        <div class="table__body">
          <div v-if="currantTable == 'table-1'" class="table-1">
            <ul v-for="(item, index) in 2" :key="index" class="border-t-[1.5px] borderBox">
              <li>
                <div class="flex items-center">
                  <div class="mr-5">
                    <img
                      class="w-[42px] h-[42px] rounded-full object-cover"
                      src="../../assets/man.png"
                      alt="image"
                    />
                  </div>
                  <div>
                    <h3>Alisher Anvarov</h3>
                    <span class="text-sm text-[#888A8F]">21.02.1981</span>
                  </div>
                </div>
              </li>
              <li>
                <h3>Marketing</h3>
              </li>
              <li>
                <h3>Marketing</h3>
              </li>
              <li>
                <div class="inline-block relative group">
                  <h3 class="link">{{$t('show')}}</h3>
                  <div
                    class="hidden group-hover:block duration-300 z-[2] absolute left-1/2 -translate-x-1/2 bottom-[-90px] mainBackgroundColorBlack w-[150px] p-4 rounded-[12px]"
                  >
                    <div class="relative w-full">
                      <span class="text-[12px] text-[#888A8F]">{{$t('salary')}}</span>
                      <p class="text-white text-sm font-semibold">
                        23,000,000 uzs
                      </p>
                      <div
                        class="z-[-1] w-[40px] h-[40px] mainBackgroundColorBlack rounded-[4px] absolute left-1/2 -translate-x-1/2 top-[-16px] rotate-45"
                      ></div>
                    </div>
                  </div>
                </div>
              </li>
              <li>
                <h3>Berilgan</h3>
              </li>
              <li>
                <h3>12.06.2022</h3>
              </li>
              <li class="relative">
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

          <div v-if="currantTable == 'table-2'" class="table-2">
            <ul v-for="(item, index) in 5" :key="index" class="border-t-[1.5px] borderBox">
              <li>
                <div class="flex items-center">
                  <div class="mr-5">
                    <img
                      class="w-[42px] h-[42px] rounded-full object-cover"
                      src="../../assets/man.png"
                      alt="image"
                    />
                  </div>
                  <div>
                    <h3>Alisher Anvarov</h3>
                    <span class="text-sm text-[#888A8F]">21.02.1981</span>
                  </div>
                </div>
              </li>
              <li v-for="(i, index) in 2" :key="index">
                <h3>Sotuvchi</h3>
              </li>
              <li>
                <div class="relative">
                  <div
                    ref="popUpRef"
                    @click="togglePopup(index)"
                    class="cursor-pointer flex justify-center w-full"
                  >
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
    <adminsModal :isModalActive="isModalActive"/>
  </section>
</template>

<script>
import { ref, onMounted } from "vue";
import adminsModal from './components/adminsModal.vue'
import PlusIcon from "@/assets/iconsVue/PlusIcon.vue";
import Table from "@/components/cards/Table.vue";
import FunctionsIcon from "@/assets/iconsVue/FunctionsIcon.vue";
import { useI18n } from 'vue-i18n'

export default {
  components: {
    useI18n,
    adminsModal,
    PlusIcon,
    Table,
    FunctionsIcon,
  },
  setup() {
    const {locale}  = useI18n()

    let currantTable = ref("table-1");
    const popUpRef = ref(null);

    let isModalActive = ref(false)
    let popUpActive = ref([false]);
    const changeTable = (e) => {
      currantTable.value = e;
    };

    const togglePopup = (index) => {
      popUpActive.value[index] = !popUpActive.value[index];
    };

    const toggleModal = () => {
      isModalActive.value = !isModalActive.value
    }

    // onMounted(() => {
    //   window.addEventListener("click", togglePopup);
    // });

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
      changeTable,
      currantTable,
      popUpActive,
      popUpRef,
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
