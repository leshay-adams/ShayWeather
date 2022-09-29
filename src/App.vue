<template>
  <div
    class="flex flex-col min-h-screen font-Roboto bg-gradient-to-b from-purple-900 to-blue-400"
  >
    <RouterView />
    <NavBar />
  </div>
</template>

<script setup>
import { RouterView } from "vue-router";
import NavBar from "./components/NavBar.vue";
</script>
