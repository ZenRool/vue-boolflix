<template>
  <header class="header container-fluid d-flex align-items-center">
    <div class="header__logo">
      <img src="../assets/img/boolflix.png" alt="logo" />
    </div>
    <div>
      <SearchMovie @searchMovie="searchMovie($event)" />
    </div>
  </header>
</template>
<script>
import SearchMovie from "./SearchMovie.vue";

export default {
  name: "MovieHeader",
  components: {
    SearchMovie,
  },
  methods: {
    searchMovie(input) {
      this.$emit("searchMovie", input);
    },
  },
};
</script>
<style lang="scss" scoped>
.header {
  height: 140px;
  &__logo {
    margin-left: calc(100% / 12);
    img {
      height: 100%;
      width: auto;
    }
  }
}
</style>
