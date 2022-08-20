<template>
  <h2>My List</h2>
  <div v-for="(anime, i) in props.myAnimeAsc" :key="i">
    <AnimeCard :anime="anime" />
    <!-- <span> {{ anime.watched_episodes }} / {{ anime.total_episodes }} </span>  -->
    <button
      @click="increaseWatch(anime)"
      v-if="anime.total_episodes !== anime.watched_episodes"
    >
      +
    </button>
    <button v-if="anime.watched_episodes > 0" @click="decreaseWatch(anime)">
      -
    </button>
    <button>delete list</button>
  </div>
</template>



<script setup>
import { onMounted } from "vue";
import AnimeCard from "./AnimeCard.vue";

const increaseWatch = (anime) => {
  anime.watched_episodes++;
  localStorage.setItem("my_animee", JSON.stringify(props.myAnime.value));
};

const decreaseWatch = (anime) => {
  anime.watched_episodes--;
  localStorage.setItem("my_animee", JSON.stringify(props.myAnime.value));
};

const props = defineProps({
  myAnimeAsc: Array,

  myAnime: Array | Object,
});

onMounted(() => {
  props.myAnime.value = JSON.parse(localStorage.getItem("my_anime")) || [];
});
</script>