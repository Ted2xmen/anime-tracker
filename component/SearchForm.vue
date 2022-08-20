<template>
  <form @submit.prevent="searchAnime">
    <input
      type="text"
      placeholder="search..."
      v-model="query"
      @input="handleInput"
    />
    <button type="submit">search</button>
  </form>
</template>


<script setup>
const props = defineProps({
  searchAnime: Function,
  query: String,
  handleInput: Function,
});
</script>