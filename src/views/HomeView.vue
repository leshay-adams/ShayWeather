<script setup>
import { ref } from "vue";

const searchQuery = ref("");
</script>

<template>
  <main>
    <div>
      <input v-model="searchQuery" type="text" placeholder="Search for a city or state" />
    </div>
  </main>
</template>
