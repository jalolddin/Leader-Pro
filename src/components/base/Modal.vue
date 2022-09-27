<template>
  <div
    @click="close"
    class="fixed top-0 left-0 w-full h-full bg-[#000] bg-opacity-[0.3] z-[99] flex items-center justify-center duration-500"
    :class="isModalActive ? 'flex' : 'hidden'"
  >
      <perfect-scrollbar class="items-center justify-center grid">
        <div ref="modalRef" class="bg-white w-[430px] relative p-4 rounded-[12px]">

            <span class="absolute right-4 top-4">
              <CancelIcon
                @click="closeModal"
                stroke="stroke-[#1d3260] rotate-45 hover:rotate-0 cursor-pointer duration-200"
                width="32"
                height="32"
              />
            </span>
            <slot name="modalHeader"></slot>

            <slot name="modalBody"></slot>

            <footer class="w-full flex items-center gap-3">
              <button
                @click="closeModal"
                class="basicBtn w-full bg-[#1d3260] bg-opacity-20 flex justify-center main-color-black mt-8 text-center hover:bg-opacity-30 duration-200"
              >
                {{$t('cancel')}}
              </button>
              <button
                @click="submit"
                class="basicBtn w-full bg-[#2597DE] flex justify-center text-white mt-8 text-center hover:bg-opacity-80 duration-200"
              >
                {{$t('сonfirm')}}
              </button>
            </footer>
        </div>
      </perfect-scrollbar>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue'
import CancelIcon from "../../assets/iconsVue/PlusIcon.vue";
export default {
  props: ['isModalActive', 'width'],
  components: {
    CancelIcon,
  },
  setup(props, context) {
    // const isModalActive = ref(false)
    const modalRef = ref(null)
    const closeModal = () => {
        // if (e.target !== modalRef.value) {
            // isModalActive.value = false
            context.emit('close')
        // }
    }

    // onMounted(() => {
    //     window.addEventListener('click', closeModal)
    // })

    return {
        closeModal,
        modalRef
    }
  },
};
</script>

<style lang="scss">

</style>