<template>
  <li class="d-flex flex-column align-items-center p-1">
    <h2>{{ movie.title }}</h2>
    <p>{{ movie.original_title }}</p>
    <img
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
      flags: ["it", "en", "jp", "de", "fr"],
    };
  },
  props: {
    movie: Object,
  },
  computed: {
    flagsIs() {
      return this.flags.includes(this.movie.original_language);
    },
  },
};
</script>
<style lang="scss" scoped>
li {
  border: 3px solid red;
  height: 300px;
  h2,
  p {
    text-align: center;
  }
  p {
    font-size: 1.5rem;
  }
  img {
    width: 60px;
    height: 40px;
  }
}
</style>
