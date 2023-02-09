<template>
  <div class="movie-detail">
    <h2>{{ movie.Title }}</h2>
    <p>{{ movie.Year }}</p>
    <img :src="movie.Poster" :alt="movie.Title" class="featured-img" />
    <p>{{ movie.Plot }}</p>
  </div>
</template>

<script>
import { ref, onBeforeMount } from "vue";
import { useRoute } from "vue-router";
import env from "@/env.js";

export default {
  setup() {
    const movie = ref({});
    const route = useRoute();

    onBeforeMount(() => {
      fetch(
        `http://www.omdbapi.com/?apikey=${env.api_key}&i=${route.params.id}&plot=full`
      )
        .then((response) => response.json())
        .then((data) => {
          movie.value = data;
        });
    });
    return {
      movie,
      route,
    };
  },
};
</script>
<style lang="scss">
.movie-detail {
  padding: 16px;
  h2 {
    color: white;
    font-size: 28px;
    font-weight: 600;
    margin-bottom: 16px;

    .featured-img {
      display: block;
      max-width: 200px;
      margin-bottom: 16px;
    }
  }
  p {
    color: white;
    font-size: 18px;
    line-height: 1.4;
  }
}
</style>
