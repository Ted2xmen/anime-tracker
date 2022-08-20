<template>
  <h2>Results</h2>
  <div class="results" v-if="searchResults.length > 0">
    <div v-for="(anime, i) in searchResults" :key="i">
      <AnimeCard :anime="anime" />

      <button @click="addAnime(anime)">add to my list</button>
    </div>
  </div>
</template>

<script>
import AnimeCard from "./AnimeCard.vue";
export default {
  props: ["searchResults", "addAnime"],
  components: { AnimeCard },
};
</script>
