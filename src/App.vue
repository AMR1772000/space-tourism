<template>
  <nav>
    <Navigation />
  </nav>
  <RouterView />
</template>

<script setup>
import { RouterView } from "vue-router";
import Navigation from "./components/Navigation.vue";
</script>
