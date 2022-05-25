<template>
  <ul class="container-fluid d-flex p-1 wrap" v-if="this.list.length !== 0">
    <MovieCard
      v-for="(movie, index) in this.list"
      :key="index"
      :movie="movie"
    />
  </ul>
</template>
<script>
import MovieCard from "./MovieCard.vue";
export default {
  name: "MovieMain",
  components: {
    MovieCard,
  },
  props: {
    list: Array,
  },
};
</script>
<style lang="scss" scoped></style>
