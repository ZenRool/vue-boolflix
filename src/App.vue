<template>
  <div id="app">
    <MovieHeader @searchMovie="searchMovie($event)" />
    <MovieMain :list="this.movieList" />
  </div>
</template>
<script>
import MovieHeader from "./components/MovieHeader.vue";
import MovieMain from "./components/MovieMain.vue";
import axios from "axios";
export default {
  name: "App",
  components: {
    MovieHeader,
    MovieMain,
  },
  data: function () {
    return {
      key: "712d751b0fecfb6d44a60386fc167499",
      movieList: [],
      serieList: [],
    };
  },
  methods: {
    searchMovie(input) {
      const options = {
        params: {
          api_key: this.key,
          query: input,
        },
      };
      axios
        .get("https://api.themoviedb.org/3/search/movie", options)
        .then((resp) => (this.movieList = resp.data.results));
    },
  },
};
</script>

<style lang="scss">
@import "./style/common.scss";
</style>
