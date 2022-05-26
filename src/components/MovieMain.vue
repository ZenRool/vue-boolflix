<template>
  <ul
    class="container-fluid d-flex p-1 wrap"
    v-if="(this.list.length !== 0) & this.complete"
  >
    <MovieCard
      v-for="(movie, index) in this.list"
      :key="letIndex + index"
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
    letIndex: String,
    complete: Boolean,
  },
};
</script>
<style lang="scss" scoped>
ul {
  padding-top: 2rem;
}
</style>
