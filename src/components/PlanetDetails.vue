<template>
  <div
    class="flex relative top-[17%] left-[18%] gap-16 xs:flex-col xs:gap-1 xs:w-[85%] xs:top-[22%] xs:left-[10%]"
    v-if="planet"
  >
    <img
      :src="planet.images.png"
      :alt="planet.name"
      class="w-[400px] h-[400px] xs:w-[200px] xs:h-[200px] xs:mt-0 xs:mx-auto mt-12 mr-12"
    />
    <div class="flex flex-col mt-2 xs:mt-0 xs:w-full">
      <h1 class="font-light text-white text-[150px] xs:text-[100px] xs:m-auto">
        {{ planet.name }}
      </h1>
      <p
        class="flex text-start w-[430px] text-[#D0D6F9] text-[17px] xs:text-sm xs:mx-auto xs:w-[350px] leading-6 mb-5"
      >
        {{ planet.description }}
      </p>
      <hr />
      <div
        class="flex gap-20 mt-5 xs:flex-col xs:gap-7 xs:justify-center xs:items-center"
      >
        <div class="flex flex-col xs:items-center">
          <h6 class="text-[#D0D6F9] text-[14px]">AVG. DISTANCE</h6>
          <p class="text-white text-[25px]">{{ planet.distance }}</p>
        </div>
        <div class="flex flex-col xs:items-center">
          <h6 class="text-[#D0D6F9] text-[14px]">EST. TRAVEL TIME</h6>
          <p class="text-white text-[25px]">{{ planet.travel }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
  planet: Object,
});
</script>
