<template>
  <div class="bg-crew h-screen overflow-hidden bg-crew-mobile">
    <div class="relative left-[13%] top-[19%] xs:top-[14%]">
      <h1 class="text-white text-[28px] xs:text-[24px] font-normal">
        <span class="mr-[10px] font-bold text-gray-600 tracking-[2px]">02</span>
        MEET YOUR CREW
      </h1>
    </div>
    <CrewDetails :crew="crew" />
  </div>
</template>

<script setup>
import CrewDetails from "@/components/CrewDetails.vue";
import axios from "axios";
import { onMounted, ref } from "vue";

const crew = ref([]);

onMounted(() => {
  axios
    .get("http://localhost:3000/crew")
    .then((response) => {
      crew.value = response.data;
    })
    .catch((error) => {
      console.error("Error Fetching crew dara: " + error);
    });
});
console.log(crew);
</script>
<style>
.bg-crew {
  background-image: url(../assets/images/crew/background-crew-desktop.jpg);
  background-size: cover;
  background-position: center;
}
@media (max-width: 575px) {
  .bg-crew-mobile {
    background-image: url("../assets/images/crew/background-crew-mobile.jpg");
    background-size: cover;
    background-position: center;
    overflow: auto;
  }
}
</style>
