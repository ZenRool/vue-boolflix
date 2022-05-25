<template>
  <li class="d-flex flex-column align-items-center p-1">
    <h2>{{ movie.title }}</h2>
    <p>{{ movie.original_title }}</p>
    <p>{{ movie.original_language }}</p>
    <p>{{ movie.vote_average }}</p>
  </li>
</template>
<script>
export default {
  name: "MovieCard",
  props: {
    movie: Object,
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
}
</style>
