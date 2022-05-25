<template>
  <div class="form d-flex align-items-center">
    <input type="text" v-model="inputMovie" placeholder="Cerca..." />
    <button class="btn-red" @click="$emit('searchMovie', inputMovie)">
      Cerca
    </button>
  </div>
</template>
<script>
export default {
  name: "SearchMovie",
  data: function () {
    return {
      inputMovie: "",
    };
  },
};
</script>
<style lang="scss" scoped>
.form {
  height: 100%;
  margin-left: 2rem;
  input {
    width: 250px;
    font-size: 1.5rem;
    padding: 0.5rem 0.8rem;
    caret-color: rgba($color: #ff0000, $alpha: 0.6);
    border-color: red;
  }
  button {
    margin-left: 1rem;
    font-size: 1.6rem;
    height: 60px;
    padding: 0 2rem;
  }
}
</style>
