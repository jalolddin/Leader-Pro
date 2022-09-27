<template>
  <div
    class="duration-300 z-[2] absolute -left-[140px] top-1/2 -translate-y-1/2 mainBackgroundColorBlack w-[150px] p-4 rounded-[12px]"
    :class="additonalClasses"
  >
    <div class="relative w-full">
      <slot name="FunctionsPopupContent"></slot>

      <div
        class="z-[-1] w-[40px] h-[40px] mainBackgroundColorBlack rounded-[4px] absolute right-[-16px] -translate-y-1/2 top-1/2 rotate-45"
      ></div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["additonalClasses"],
};
</script>

<style scoped>
li {
  width: auto !important;
}
</style>
