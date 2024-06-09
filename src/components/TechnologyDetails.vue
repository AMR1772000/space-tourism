<template>
  <div
    v-if="technology"
    class="text-white flex items-center xs:flex-col xs:justify-center xs:gap-6 xs:mt-5"
  >
    <div class="w-[48%] xs:w-full xs:text-center order-2 xs:px-3">
      <P class="text-[#D0D6F9] text-lg xs:text-sm">THE TERMINOLOGY ...</P>
      <h1 class="text-[60px] tracking-widest xs:text-[35px] xs:mb-3 xs:mt-2">
        {{ technology.name }}
      </h1>
      <p class="text-[#d0d6f9] text-sm w-[75%] pr-6 xs:w-full xs:pr-0">
        {{ technology.description }}
      </p>
    </div>

    <div class="ml-8 xs:ml-0 order-1 xs:mb-3">
      <img
        :src="technology.images.portrait"
        :alt="technology.name"
        class="h-[450px] desktop"
      />
      <img
        :src="technology.images.landscape"
        :alt="technology.name"
        class="mobile"
      />
    </div>
  </div>
</template>

<script setup>
import { defineProps } from "vue";
const props = defineProps({
  technology: {
    type: Object,
    required: true,
  },
});
</script>
<style>
.desktop {
  display: flex;
}
.mobile {
  display: none;
}
@media (max-width: 975px) {
  .desktop {
    display: none;
  }
  .mobile {
    display: flex;
  }
}
</style>
