<script setup>
import { ref, computed, onMounted } from "vue";
import SearchResults from "../component/SearchResults.vue";
import MyList from "../component/MyList.vue";
import SearchForm from "../component/SearchForm.vue";

import { useAppStore } from "./store.js";

const useStore = useAppStore();

const my_anime = ref([]);
const search_results = ref([]);

const my_anime_asc = computed(() => {
  return my_anime.value.sort((a, b) => {
    return a.title.localeCompare(b.title);
  });
});

const searchAnime = () => {
  const url = "https://api.jikan.moe/v4/anime?q=" + useStore.queryString;
  fetch(url)
    .then((res) => res.json())
    .then((res) => {
      search_results.value = res.data;
    });
};

const handleInput = (e) => {
  if (!e.target.value) {
    search_results.value = [];
  }
};

const addAnime = (anime) => {
  search_results.value = [];
  query.value = "";

  my_anime.value.push({
    id: anime.mal_id,
    title: anime.title,
    image: anime.images.jpg.image_url,
    rank: anime.rank,
    rating: anime.rating,
    total_episodes: anime.episodes,
    watched_episodes: 0,
    year: anime.year,
    score: anime.score,
    duration: anime.duration,
    scored_by: anime.scored_by,
    japanese: anime.title_japanese,
    synopsis: anime.synopsis,
  });

  localStorage.setItem("my_anime", JSON.stringify(my_anime.value));
};

onMounted(() => {
  my_anime.value = JSON.parse(localStorage.getItem("my_anime")) || [];
});
</script>



<template>
  <div>
    <SearchForm :searchAnime="searchAnime" :handleInput="handleInput" />
    <SearchResults :searchResults="search_results" :addAnime="addAnime" />
    <MyList :myAnimeAsc="my_anime_asc" :myAnime="my_anime" />
  </div>
</template>


