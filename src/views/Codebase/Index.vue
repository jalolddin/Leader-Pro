<template>
  <section class="pb-20">
    <div class="pt-10 pb-8 wrapper">
      <h3 class="sectionTitle">
        {{
          currantTable === "table-1"
            ? $t('codebase')
            : currantTable === "table-2"
            ? $t('codebase')
            : currantTable === "table-3"
            ? $t('codebase')
            : $t('codebase')
        }}
      </h3>
      <!-- <span class="text-sm text-[#888A8F] mt-2">245 ta</span> -->
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
          {{$t('foam')}}
        </li>
        <li
          @click="changeTable('table-2')"
          class="mainColor font-medium duration-300"
          :class="currantTable === 'table-2' ? 'active' : ''"
        >
          {{$t('sponge')}}
        </li>
        <li
          @click="changeTable('table-3')"
          class="mainColor font-medium duration-300"
          :class="currantTable === 'table-3' ? 'active' : ''"
        >
          {{$t('Mattress')}}
        </li>
        <li
          @click="changeTable('table-4')"
          class="mainColor font-medium duration-300"
          :class="currantTable === 'table-4' ? 'active' : ''"
        >
          {{$t('pillow')}}
        </li>
        <li
          @click="changeTable('table-5')"
          class="mainColor font-medium duration-300"
          :class="currantTable === 'table-5' ? 'active' : ''"
        >
          {{$t('curly_cutting')}}
        </li>
      </ul>

      <button
        @click="toggleModal"
        :class="currantTable === 'table-5' ? 'opacity-0' : ''"
        class="mainBackgroundColor hover:scale-105 duration-300 text-white basicBtn"
      >
        <PlusIcon stroke="stroke-current mr-2" />
        {{$t('add')}}
      </button>
    </div>

    <div class="a-table">
      <div class="table-3 pt-5" v-if="currantTable === 'table-1'">
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
                            <h3 class="a-table-title">{{$t('code')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('type')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('name')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title flex justify-center">{{$t('actions')}}</h3>
                          </li>
                        </ul>
                      </div>

                      <div class="a-card-body">
                        <ul
                          v-for="(item, index) in 5"
                          class="uk-grid-collapse uk-child-width-expand py-5 border-t-[1.5px] borderBox"
                          uk-grid
                          :key="index"
                        >
                          <li>
                            <h3 class="a-table-text">#FFFFFFF</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">FGT 32P</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">Oq porolon</h3>
                          </li>
                          <li>
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
                            </div>
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
                            <h3 class="a-table-title">{{$t('code')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('type')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('name')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title flex justify-center">{{$t('actions')}}</h3>
                          </li>
                        </ul>
                      </div>

                      <div class="a-card-body">
                        <ul
                          v-for="(item, index) in 5"
                          class="uk-grid-collapse uk-child-width-expand py-5 border-t-[1.5px] borderBox"
                          uk-grid
                          :key="index"
                        >
                          <li>
                            <h3 class="a-table-text">#FFFFFFF</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">UHER VFR</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">
                              Qattiq tosh {{ item + 1 }}m
                            </h3>
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

      <div class="table-4 pt-5" v-if="currantTable === 'table-2'">
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
                            <h3 class="a-table-title">{{$t('code')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('type')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('name')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title flex justify-center">{{$t('actions')}}</h3>
                          </li>
                        </ul>
                      </div>

                      <div class="a-card-body">
                        <ul
                          v-for="(item, index) in 2"
                          class="uk-grid-collapse uk-child-width-expand py-5 border-t-[1.5px] borderBox"
                          uk-grid
                          :key="index"
                        >
                          <li>
                            <h3 class="a-table-text">#FFFFFFF</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">Ximiya FRT</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">Oq DDP suyuqlik</h3>
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
                            <h3 class="a-table-title">{{$t('code')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('type')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('name')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title flex justify-center">{{$t('actions')}}</h3>
                          </li>
                        </ul>
                      </div>

                      <div class="a-card-body">
                        <ul
                          v-for="(item, index) in 2"
                          class="uk-grid-collapse uk-child-width-expand py-5 border-t-[1.5px] borderBox"
                          uk-grid
                          :key="index"
                        >
                          <li>
                            <h3 class="a-table-text">#FFFFFFF</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">Ximiya PPU</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">Bisvol 22DT</h3>
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

      <div class="table-4 pt-5" v-if="currantTable === 'table-3'">
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
                            <h3 class="a-table-title">{{$t('code')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('type')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('name')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title flex justify-center">{{$t('actions')}}</h3>
                          </li>
                        </ul>
                      </div>

                      <div class="a-card-body">
                        <ul
                          v-for="(item, index) in 2"
                          class="uk-grid-collapse uk-child-width-expand py-5 border-t-[1.5px] borderBox"
                          uk-grid
                          :key="index"
                        >
                          <li>
                            <h3 class="a-table-text">#FFFFFFF</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">PALE 21D</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">Oq DDP suyuqlik</h3>
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
                            <h3 class="a-table-title">{{$t('code')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('type')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('name')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title flex justify-center">{{$t('actions')}}</h3>
                          </li>
                        </ul>
                      </div>

                      <div class="a-card-body">
                        <ul
                          v-for="(item, index) in 2"
                          class="uk-grid-collapse uk-child-width-expand py-5 border-t-[1.5px] borderBox"
                          uk-grid
                          :key="index"
                        >
                          <li>
                            <h3 class="a-table-text">#FFFFFFF</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">Ximiya EER</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">Bisvol 22DT</h3>
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
                          <li>
                            <h3 class="a-table-title">{{$t('code')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('type')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('name')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title flex justify-center">{{$t('actions')}}</h3>
                          </li>
                        </ul>
                      </div>

                      <div class="a-card-body">
                        <ul
                          v-for="(item, index) in 2"
                          class="uk-grid-collapse uk-child-width-expand py-5 border-t-[1.5px] borderBox"
                          uk-grid
                          :key="index"
                        > 
                          <li>
                            <h3 class="a-table-text">#FFFFFFF</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">Ximiya CVX</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">Oq DDP suyuqlik</h3>
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
                            <h3 class="a-table-title">{{$t('code')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('type')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('name')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title flex justify-center">{{$t('actions')}}</h3>
                          </li>
                        </ul>
                      </div>

                      <div class="a-card-body">
                        <ul
                          v-for="(item, index) in 2"
                          class="uk-grid-collapse uk-child-width-expand py-5 border-t-[1.5px] borderBox"
                          uk-grid
                          :key="index"
                        >
                          <li>
                            <h3 class="a-table-text">#FFFFFFF</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">Ximiya 21D</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">Bisvol 22DT</h3>
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







      <div class="table-4 pt-5" v-if="currantTable === 'table-5'">
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
                            <h3 class="a-table-title">{{$t('code')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('type')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('name')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title flex justify-center">{{$t('actions')}}</h3>
                          </li>
                        </ul>
                      </div>

                      <div class="a-card-body">
                        <ul
                          v-for="(item, index) in 2"
                          class="uk-grid-collapse uk-child-width-expand py-5 border-t-[1.5px] borderBox"
                          uk-grid
                          :key="index"
                        >
                          <li>
                            <h3 class="a-table-text">#FFFFFFF</h3>
                          </li>
                           <li>
                            <h3 class="a-table-text">Ximiya LLK</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">Oq DDP suyuqlik</h3>
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
                            <h3 class="a-table-title">{{$t('code')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('type')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title">{{$t('name')}}</h3>
                          </li>
                          <li>
                            <h3 class="a-table-title flex justify-center">{{$t('actions')}}</h3>
                          </li>
                        </ul>
                      </div>

                      <div class="a-card-body">
                        <ul
                          v-for="(item, index) in 2"
                          class="uk-grid-collapse uk-child-width-expand py-5 border-t-[1.5px] borderBox"
                          uk-grid
                          :key="index"
                        >
                          <li>
                            <h3 class="a-table-text">#FFFFFFF</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">Ximiya 221</h3>
                          </li>
                          <li>
                            <h3 class="a-table-text">Bisvol 22DT</h3>
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











  <Modal :isModalActive="isModalActive" @close="toggleModal">
    <template v-slot:modalHeader>
      <h3 class="text-lg font-medium text-center main-color-black">
        {{$t('new_product_code')}}
      </h3>
    </template>

    <template v-slot:modalBody>
      <div class="mt-4 space-y-3">

        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="../../assets/icons/Number.svg"
            alt="user"
          />
          <input
            type="text"
            name="text"
            autocomplete="off"
            required
            :placeholder="$t('date')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
          />
        </div>

        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="../../assets/icons/Number.svg"
            alt="user"
          />
          <input
            type="text"
            name="text"
            autocomplete="off"
            required
            :placeholder="$t('category')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
          />
        </div>

        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="../../assets/icons/Number.svg"
            alt="user"
          />
          <input
            type="text"
            name="text"
            autocomplete="off"
            required
            :placeholder="$t('type')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
          />
        </div>

        <div class="relative">
          <img
            class="absolute left-4 top-1/2 -translate-y-1/2"
            src="../../assets/icons/Number.svg"
            alt="user"
          />
          <input
            type="text"
            name="text"
            autocomplete="off"
            required
            :placeholder="$t('name')"
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
            :placeholder="$t('code')"
            class="mt-1 w-full py-[14px] px-[24px] pl-12 focus:outline-none mainColor border borderBox rounded-[12px] text-lg"
          />
        </div>
      </div>
    </template>
  </Modal>


  </section>
</template>

<script>
import { ref } from "vue";
import Modal from '@/components/base/Modal.vue'
import PlusIcon from "@/assets/iconsVue/PlusIcon.vue";
import SmallArrowRight from "@/assets/iconsVue/SmallArrowRight.vue";
import FunctionsIcon from "@/assets/iconsVue/FunctionsIcon.vue";

export default {
  components: {
    Modal,
    SmallArrowRight,
    PlusIcon,
    FunctionsIcon,
  },
  setup() {
    let currantTable = ref("table-1");
    let isModalActive = ref(false)

    const params = ref({
      page: 1,
    });

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

    function updatePage(value) {
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
