<template>
  <ul
    class="container-fluid d-flex p-1 wrap"
    v-if="this.listMo.length + this.listSe.length !== 0"
  >
    <MovieCard
      v-for="(movie, index) in this.listMo"
      :key="index"
      :movie="movie"
      :isMovie="true"
    />
    <MovieCard
      v-for="(serie, index) in this.listSe"
      :key="index + 100"
      :movie="serie"
      :isMovie="false"
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
    listMo: Array,
    listSe: Array,
  },
};
</script>
<style lang="scss" scoped></style>
