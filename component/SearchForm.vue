<script setup>
import { useAppStore } from "../src/store.js";

const useStore = useAppStore();

const props = defineProps({
  searchAnime: Function,
  handleInput: Function,
});
</script>

<template>
  <form @submit.prevent="searchAnime">
    <input
      type="text"
      placeholder="search..."
      v-model="useStore.queryString"
      @input="handleInput"
    />
    <button type="submit">search</button>
  </form>
</template>


