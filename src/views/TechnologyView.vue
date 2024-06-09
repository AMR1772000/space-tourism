<template>
  <div class="bg-technology h-screen overflow-hidden bg-technology-mobile">
    <div class="relative left-[13%] top-[19%] xs:top-[14%]">
      <h1 class="text-white text-[28px] xs:text-[24px]">
        <span class="mr-[10px] font-bold text-gray-600 tracking-[2px]">03</span>
        SPACE LAUNCH 101
      </h1>
    </div>
    <div
      class="flex flex-row relative left-[13%] top-[20%] gap-12 items-center mb-10 xs:flex-col xs:left-[0%] xs:top-[17%] xs:gap-6"
    >
      <TechnologyButtons
        :selectTechnology="selectTechnology"
        :technologies="technologies"
      />
      <TechnologyDetails :technology="selectedTechnology" />
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue";
import TechnologyButtons from "../components/TechnologyButtons.vue";
import TechnologyDetails from "../components/TechnologyDetails.vue";

import axios from "axios";

const technologies = ref([]);
const selectedTechnology = ref(null);
const selectTechnology = (idx) => {
  selectedTechnology.value = technologies.value[idx];
  console.log(selectedTechnology);
};
onMounted(() => {
  axios
    .get("http://localhost:3000/technology")
    .then((response) => {
      technologies.value = response.data;
      if (technologies.value.length > 1) {
        selectTechnology(0);
      }
    })
    .catch((error) => {
      console.error("Error Fetching Technology Data");
    });
  console.log(technologies);
});
</script>
<style>
.bg-technology {
  background-image: url(../assets/images/technology/background-technology-desktop.jpg);
  background-size: cover;
  background-position: center;
}
@media (max-width: 975px) {
  .bg-technology-mobile {
    background-image: url(../assets/images/technology/background-technology-mobile.jpg);
    background-size: cover;
    background-position: center;
    overflow: auto;
  }
}
</style>
