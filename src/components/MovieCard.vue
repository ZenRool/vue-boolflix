<template>
  <li
    class="d-flex flex-column align-items-center p-1"
    :class="isMovie ? 'movieCard' : 'seriesCard'"
  >
    <img
      class="movieImage"
      :src="
        movie.poster_path
          ? `https://image.tmdb.org/t/p/w342${movie.poster_path}`
          : require('../assets/img/poster.png')
      "
      alt="Movie image"
    />
    <h2>{{ cardName }}</h2>
    <p>{{ cardOName }}</p>
    <img
      class="flag"
      v-if="flagsIs"
      :src="require(`../assets/img/${movie.original_language}.svg`)"
      alt="flag"
    />
    <p v-else>{{ movie.original_language }}</p>
    <p>{{ movie.vote_average }}</p>
  </li>
</template>
<script>
export default {
  name: "MovieCard",
  data: function () {
    return {
      flags: ["it", "en", "ja", "de", "fr"],
    };
  },
  props: {
    movie: Object,
    isMovie: Boolean,
  },
  computed: {
    flagsIs() {
      return this.flags.includes(this.movie.original_language);
    },
    cardName() {
      return this.movie.title ? this.movie.title : this.movie.name;
    },
    cardOName() {
      return this.movie.original_title
        ? this.movie.original_title
        : this.movie.original_name;
    },
  },
};
</script>
<style lang="scss" scoped>
li.movieCard {
  border: 3px solid red;
}
li.seriesCard {
  border: 3px solid green;
}
li {
  height: 400px;
  h2,
  p {
    text-align: center;
  }
  p {
    font-size: 1.5rem;
  }
  .flag {
    width: 30px;
    height: auto;
    border: 1px solid black;
  }
  .movieImage {
    height: 50%;
    width: auto;
  }
}
</style>
