<template>
  <div class="relative top-[20%] left-[55%] xs:left-[16%] xs:top-[20%]">
    <ul
      class="flex items-center h-7 gap-7 xs:gap-4 font-barlow text-xs font-light tracking-widest text-white text-[22px]"
    >
      <li
        v-for="(planet, index) in planets"
        :key="index"
        :class="{ 'active-nav': selectedIndex === index }"
        class="pb-2 hover-nav"
      >
        <button @click="selectPlanet(index)">
          {{ planet.name }}
        </button>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { defineProps, ref, onMounted } from "vue";

const props = defineProps({
  planets: {
    type: Array,
    required: true,
  },
  selectPlanet: {
    type: Function,
    required: true,
  },
});
const selectedIndex = ref(0);

const selectPlanet = (index) => {
  selectedIndex.value = index;
  props.selectPlanet(index);
};
onMounted(() => {
  props.selectPlanet(selectedIndex.value);
});
</script>
<style scoped>
.hover-nav:hover {
  border-bottom: 3px gray solid;
  transition: all 0.5s ease;
}
.active-nav {
  border-bottom: 3px white solid; /* Adjust styling for active item */
}
</style>
