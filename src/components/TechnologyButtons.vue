<template>
  <div
    class="flex flex-col gap-8 w-[10%] xs:flex-row xs:w-full xs:gap-5 xs:justify-center"
  >
    <button
      v-for="(technology, index) in technologies"
      :key="index"
      @click="handleButtonClick(index)"
      :class="[
        'w-14 h-14 rounded-full border border-solid text-2xl xs:w-11 xs:h-11',
        selectedButtonIndex === index ? 'selected-button' : 'default-button',
      ]"
    >
      {{ index + 1 }}
    </button>
  </div>
</template>

<script setup>
import { defineProps, ref } from "vue";
const props = defineProps({
  selectTechnology: {
    type: Function,
    required: true,
  },
  technologies: {
    type: Array,
    required: true,
  },
});
const selectedButtonIndex = ref(0);

const handleButtonClick = (index) => {
  selectedButtonIndex.value = index;
  props.selectTechnology(index);
};
</script>
<style scoped>
.default-button {
  color: white;
  transition: all 0.2s ease;
}

.default-button:hover {
  border-width: 3px;
}

.default-button:active {
  color: black;
  background-color: white;
}

.selected-button {
  background-color: white;
  color: black;
}
</style>
