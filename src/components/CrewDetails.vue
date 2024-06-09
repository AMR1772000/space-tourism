<template>
  <swiper
    :space-between="25"
    :pagination="paginationOptions"
    :modules="modules"
    class="mySwiper relative mySwiper-mobile top-[26%] xs:top-[19%]"
  >
    <swiper-slide v-for="person in crew" :key="person.id">
      <div class="flex w-full gap-12 xs:flex-col xs:gap-2">
        <!-- Person Data -->
        <div
          class="flex flex-col w-[60%] px-4 mt-8 xs:w-full xs:px-0 xs:items-center xs:order-2"
        >
          <h3 class="text-[32px] xs:text-[28px] text-gray-400 font-light">
            {{ person.role }}
          </h3>
          <h1
            class="text-[45px] xs:text-[30px] xs:tracking-normal tracking-widest font-normal text-white mb-2 mt-1"
          >
            {{ person.name }}
          </h1>
          <p class="text-[#D0D6F9] text-sm w-[78%] xs:w-full xs:text-center">
            {{ person.bio }}
          </p>
        </div>
        <!-- Person Image -->
        <div
          class="w-[30%] flex justify-center items-center xs:w-full xs:order-1"
        >
          <img
            :src="person.images.png"
            :alt="person.name"
            class="w-[380px] h-[500px] xs:w-[250px] xs:h-[300px]"
          />
        </div>
      </div>
    </swiper-slide>
    <!-- Pagination Element -->
    <div class="pagination-container pagination-container-mobile"></div>
  </swiper>
</template>

<script setup>
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from "swiper/vue";
import { Pagination } from "swiper/modules";
// Import Swiper styles
import "swiper/css";
import "swiper/css/pagination";
import { defineProps } from "vue";

const props = defineProps({
  crew: {
    type: Array,
    required: true,
  },
});

const modules = [Pagination];

const paginationOptions = {
  clickable: true,
  el: ".pagination-container",
  bulletClass: "swiper-pagination-bullet",
  bulletActiveClass: "swiper-pagination-bullet-active",
};
</script>

<style>
.mySwiper {
  width: 70%;
  height: 70%;
}
@media (max-width: 975px) {
  .mySwiper-mobile {
    width: 75%;
    height: 75%;
  }
}
.mySwiper .pagination-container {
  position: absolute;
  top: 70%;
  left: 2%;
  display: flex;
  gap: 10px;
  cursor: pointer;
  z-index: 100;
}
@media (max-width: 975px) {
  .mySwiper .pagination-container-mobile {
    top: 98%;
    left: 30%;
    display: flex;
    position: absolute;
    gap: 10px;
    cursor: pointer;
    z-index: 100;
  }
}

/* Custom styles for the pagination bullets */
.swiper-pagination-bullet {
  width: 12px;
  height: 12px;
  background-color: rgb(79, 79, 79);
  opacity: 1;
}

.swiper-pagination-bullet-active {
  background-color: #fff;
}
</style>
