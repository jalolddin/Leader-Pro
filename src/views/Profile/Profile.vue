<template>
  <div class="mt-5">
    <div class="flex items-center space-x-5 mt-10 wrapper">
      <div class="border w-16 h-16 rounded-full overflow-hidden">
        <img
          src="../../assets/man.png"
          alt=""
          class="w-full h-full object-cover cursor-pointer"
        />
      </div>
      <div>
        <p class="mainColor text-lg font-[700]">Huzayfa Bahromoglu</p>
        <span class="text-sm font-medium mainColorText">Super admin</span>
      </div>
    </div>

    <div class="py-10 flex items-center space-x-8 wrapper">
      <div
        class="border borderBox flex items-center rounded-[12px] py-5 px-6 space-x-6"
      >
        <img src="../../assets/icons/phone.svg" alt="icon" />
        <div>
          <span class="text-sm text-[#888A8F]">{{$t('phone_number')}}</span>
          <div class="flex space-x-6 mt-2">
            <p v-if="!changePhone" class="mainColor font-semibold w-[180px]">
              +998 90 900-49-38
            </p>
            <input
              ref="PhoneInputRef"
              v-if="changePhone"
              type="text"
              name="text"
              autocomplete="off"
              required
              value="+998"
              class="focus:outline-none mainColor placeholder:text-[#141839] font-semibold w-[180px]"
            />
            <span
              @click="changePhoneNumber"
              class="cursor-pointer mainColorText mainBorderColor font-medium border-b borderBox"
            >
             {{ changePhone ? $('cancel') : $t('change')}}
            </span>
          </div>
        </div>
      </div>
      <div
        class="border borderBox flex items-center rounded-[12px] py-5 px-6 space-x-6"
      >
        <img src="../../assets/icons/phone.svg" alt="icon" />
        <div>
          <span class="text-sm text-[#888A8F]">{{$t('password')}}</span>
          <div class="flex space-x-6 mt-2">
            <p
              v-if="!password"
              class="mainColor font-semibold w-[110px] flex items-center"
            >
              **********
            </p>
            <input
              ref="PasswordInputRef"
              v-if="password"
              type="text"
              name="text"
              autocomplete="off"
              required
              value="password"
              class="focus:outline-none mainColor placeholder:text-[#141839] font-semibold w-[110px]"
            />
            <span
              @click="changePassword"
              class="cursor-pointer mainColorText mainBorderColor font-medium border-b borderBox"
            >
              {{ password ? 'Bekor qilish' : $t('change')}}
            </span>
          </div>
        </div>
      </div>
    </div>

    <div class="py-10 border-t-[1.5px] borderBox wrapper">
      <h3 class="sectionTitle">{{$t('profile_settings')}}</h3>
      <div class="mt-8 grid grid-cols-2 gap-8 w-1/2">
        <div class="form-input-anim">
          <input
            type="text"
            name="text"
            autocomplete="off"
            required
            class="w-full py-[14px] px-[24px] focus:outline-none mainColor border borderBox rounded-[12px]"
          />
          <label for="text" class="label-name">
            <span class="content-name">{{$t('your_name')}}</span>
          </label>
        </div>
        <div class="form-input-anim">
          <input
            type="text"
            name="text"
            autocomplete="off"
            required
            class="w-full py-[14px] px-[24px] focus:outline-none mainColor border borderBox rounded-[12px]"
          />
          <label for="text" class="label-name">
            <span class="content-name">{{$t('your_last_name')}}</span>
          </label>
        </div>
        <div>
          <Datepicker v-model="date" :placeholder="$t('date')"></Datepicker>
        </div>
        <div>
          <div
            class="w-full h-[56px] border-[1.5px] borderBox rounded-[12px] relative"
          >
            <div
              ref="genderSelectRef"
              class="w-full h-full absolute left-0 top-0 cursor-pointer"
            ></div>
            <div class="flex text-[#888a8f] py-[14px] px-[24px]">
              <span>{{ currentGender }}</span>
              <img
                :class="genderSelectDropdownActive ? 'rotate-180' : ''"
                class="absolute right-4 top-1/2 -translate-y-1/2"
                src="../../assets/icons/smallArrowBottom.svg"
                alt="img"
              />
            </div>
            <ul
              :class="
                genderSelectDropdownActive
                  ? 'opacity-100 z-10 h-[110px]'
                  : 'opacity-0 z-[-1] h-[0px]'
              "
              class="absolute left-1/2 -translate-x-1/2 top-[64px] mainBackgroundColorBlack w-full scroll-none overflow-scroll p-4 rounded-[12px] text-white duration-300"
            >
              <li
                v-for="gender in genderList"
                :key="gender"
                @click="handleGender(gender)"
                class="py-1.5 cursor-pointer text-lg flex items-center justify-between"
                :class="currentGender == gender ? 'mainColorText' : ''"
              >
                {{ gender }}
                <CheckedIcon
                  v-if="currentGender == gender"
                  fill="fill-[#5FC7D1]"
                  width="18"
                />
              </li>
            </ul>
          </div>
        </div>
        <!--<div class="form-input-anim">
          <input
            type="text"
            name="text"
            autocomplete="off"
            required
            class="w-full py-[14px] px-[24px] focus:outline-none mainColor border borderBox rounded-[12px]"
          />
          <label for="text" class="label-name">
            <span class="content-name">Tug‘ilgan sana</span>
          </label>
        </div> 
        <div class="form-input-anim">
          <input
            type="text"
            name="text"
            autocomplete="off"
            required
            class="w-full py-[14px] px-[24px] focus:outline-none mainColor border borderBox rounded-[12px]"
          />
          <label for="text" class="label-name">
            <span class="content-name">Jinsingiz</span>
          </label>
        </div>-->
      </div>
    </div>

    <div class="py-10 border-t-[1.5px] borderBox wrapper">
      <h3 class="sectionTitle">{{$t('program_settings')}}</h3>
      <div class="mt-8 grid grid-cols-2 gap-8 w-1/2">
        <div>
          <div
            class="w-full h-[56px] border-[1.5px] borderBox rounded-[12px] relative"
          >
            <div
              ref="languageSelectRef"
              class="w-full h-full absolute left-0 top-0 cursor-pointer"
            ></div>
            <div class="flex text-[#888a8f] py-[14px] px-[24px]">
              <span>{{ currentLang }}</span>
              <img
                :class="languageSelectDropdownActive ? 'rotate-180' : ''"
                class="absolute right-4 top-1/2 -translate-y-1/2"
                src="../../assets/icons/smallArrowBottom.svg"
                alt="img"
              />
            </div>
            <ul
              :class="
                languageSelectDropdownActive
                  ? 'opacity-100 z-10 h-[110px]'
                  : 'opacity-0 z-[-1] h-[0px]'
              "
              class="absolute left-1/2 -translate-x-1/2 top-[64px] mainBackgroundColorBlack w-full scroll-none overflow-scroll p-4 rounded-[12px] text-white duration-300"
            >
              <li
                v-for="lang in languagesList"
                :key="lang"
                @click="handleLanguage(lang)"
                class="py-1.5 cursor-pointer text-lg flex items-center justify-between"
                :class="currentLang == lang ? 'mainColorText' : ''"
              >
                {{ lang }}
                <CheckedIcon
                  v-if="currentLang == lang"
                  fill="fill-[#5FC7D1]"
                  width="18"
                />
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>

    <div class="py-10 border-t-[1.5px] borderBox wrapper">
      <h3 class="sectionTitle">{{$t('notifications')}}</h3>
      <div class="mt-8">
        <div class="animateForm">
          <div>
            <label class="relative cursor-pointer">
              <input
                class="uk-checkbox absolute top-1 left-0"
                id="formcheck"
                type="checkbox"
              />
              <!-- <p class="ml-8 text-sm font-medium mainColor">
                Bildirishnomalar kelishiga ruhsat berish
              </p> -->
              <p class="ml-8 text-sm font-medium mainColor">
                Разрешить уведомления
              </p>
            </label>
          </div>
        </div>
      </div>

      <button
        class="mainBackgroundColor hover:scale-105 duration-200 text-white mt-16 basicBtn"
      >
        {{$t('сonfirm')}}
      </button>
      <!--
      <button
        @click="calcelFormSubmit"
        class="ml-5 bg-[#1d3260] bg-opacity-20 hover:scale-105 duration-200 text-[#1d3260] text-opacity-70 mt-16 basicBtn"
      >
        Bekor qilish
      </button>
      -->
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
import CheckedIcon from "../../assets/iconsVue/CheckedIcon.vue";
import { useI18n } from 'vue-i18n'

export default {
  components: {
    CheckedIcon,
  },
  setup() {
    const { locale }  = useI18n()
    let changePhone = ref(false);
    const password = ref(false);
    const PhoneInputRef = ref(null);
    const PasswordInputRef = ref(null);
    const genderSelectRef = ref(null);
    const genderSelectDropdownActive = ref(false);
    const currentGender = ref("Ваш пол");
    const genderList = ["Erkak", "Ayol"];

    const languageSelectRef = ref(null);
    const languageSelectDropdownActive = ref(false);
    const currentLang = ref("Язык");
    const languagesList = ["O'zbekcha", "Русский"];

    const changePhoneNumber = () => {
      changePhone.value = !changePhone.value;
      setTimeout(() => {
        PhoneInputRef.value.focus();
      }, 300);
    };

    const changePassword = () => {
      password.value = !password.value;
      setTimeout(() => {
        PasswordInputRef.value.focus();
      }, 300);
    };

    // const calcelFormSubmit = () => {
    //   changePhone.value = false;
    //   password.value = false;
    //   setTimeout(() => {
    //     window.scrollTo(0, 0);
    //   }, 300);
    // };

    const handleGender = (e) => {
      currentGender.value = e;
    };

    const handleLanguage = (e) => {
      if(e == "O'zbekcha"){
        locale.value = 'uz'
      }else{
        locale.value = 'ru'
      }
      currentLang.value = e;
    };

    const openDropDown = (e) => {
      e.target === genderSelectRef.value
        ? (genderSelectDropdownActive.value = true)
        : (genderSelectDropdownActive.value = false);

      if (e.target === languageSelectRef.value) {
        languageSelectDropdownActive.value = true
      } else {
        languageSelectDropdownActive.value = false
      }
    };

    onMounted(() => {
      window.addEventListener("click", openDropDown);
    });

    const date = ref(null);

    return {
      changePhone,
      PhoneInputRef,
      changePhoneNumber,
      changePassword,
      password,
      PasswordInputRef,
      date,
      currentGender,
      handleGender,
      genderList,
      genderSelectRef,
      genderSelectDropdownActive,
      languagesList,
      languageSelectDropdownActive,
      languageSelectRef,
      currentLang,
      handleLanguage,
    };
  },
};
</script>

<style></style>
