<template>
  <div class="container">
    <h3>{{ anime.title }}</h3>
    <p>Rank: {{ anime.rank }}</p>
    <span> {{ anime.watched_episodes }} / {{ anime.total_episodes }} </span>
    <img :src="anime.image || `https://via.placeholder.com/150/250 `" alt="" />
    <p>
      {{ anime.title_japanese }}
      {{ anime.duration }}
    </p>

    <div>{{ anime.score }} by {{ anime.scored_by }}</div>
    <p>{{ anime.rating }}</p>

    <p>{{ anime.synopsis }}</p>
  </div>
</template>

<script setup>
const props = defineProps({
  anime: Object,
});
</script>

<style lang="scss" scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
