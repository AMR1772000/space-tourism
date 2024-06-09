<template>
  <div class="h-screen bg-dest overflow-hidden bg-dest-mobile">
    <div class="relative left-[13%] top-[19%] xs:top-[14%]">
      <h1 class="text-white text-[28px] xs:text-[24px]">
        <span class="mr-[10px] font-bold text-gray-600 tracking-[2px]">01</span>
        PICK YOUR DESTINATION
      </h1>
    </div>
    <DestinationNav :planets="planets" :selectPlanet="selectPlanet" />
    <PlanetDetails :planet="selectedPlanet" />
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import axios from "axios";

import DestinationNav from "../components/DestinationNav.vue";
import PlanetDetails from "../components/PlanetDetails.vue";

const planets = ref([]);
const selectedPlanet = ref(null);

const selectPlanet = (index) => {
  selectedPlanet.value = planets.value[index];
};
onMounted(() => {
  axios
    .get("/public/Data/data.json")
    .then((response) => {
      planets.value = response.data.destinations;
      if (planets.value.length > 0) {
        selectPlanet(0); // Select the first planet by default
      }
    })
    .catch((error) => {
      console.error("Error fetching planets:", error);
    });
});
console.log(planets);
</script>

<style>
.bg-dest {
  background-image: url("../assets/images/destination/background-destination-desktop.jpg");
  background-size: cover;
  background-position: center;
}
@media (max-width: 575px) {
  .bg-dest-mobile {
    background-image: url("../assets/images/destination/background-destination-mobile.jpg");
    background-size: cover;
    background-position: center;
    overflow: auto;
  }
}
</style>
