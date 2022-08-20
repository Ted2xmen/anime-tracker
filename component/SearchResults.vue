<template>
  <h2>Results</h2>
  <div class="results" v-if="searchResults.length > 0">
    <div v-for="(anime, i) in searchResults" :key="i">
      <h3>{{ anime.title }}</h3>
      <p>Rank: {{ anime.rank }}</p>
      <button @click="addAnime(anime)">add to my list</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["searchResults", "addAnime"],
};
</script>
