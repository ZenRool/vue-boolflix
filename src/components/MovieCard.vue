<template>
  <li>
    <div class="inner">
      <section class="front">
        <img
          class="movieImage"
          :src="
            movie.poster_path
              ? `https://image.tmdb.org/t/p/w342${movie.poster_path}`
              : require('../assets/img/poster.png')
          "
          alt="Movie image"
        />
      </section>
      <section class="p-1 back d-flex flex-column align-items-center">
        <h2>{{ cardName }}</h2>
        <p>{{ cardOName }}</p>
        <img
          class="flag"
          v-if="flagsIs"
          :src="require(`../assets/img/${movie.original_language}.svg`)"
          alt="flag"
        />
        <p v-else>{{ movie.original_language }}</p>
        <p class="star">
          <span v-for="n in filledStars" :key="n">
            <i class="fas fa-star"></i>
          </span>
          <span v-if="isOdd">
            <i class="fas fa-star-half-alt"></i>
          </span>
          <span
            v-for="n in 5 - filledStars - isOdd"
            :key="n + filledStars + isOdd"
          >
            <i class="far fa-star"></i>
          </span>
        </p>
        <p class="description">{{ movie.overview }}</p>
      </section>
    </div>
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
    filledStars() {
      return Math.floor(this.movie.vote_average / 2);
    },
    isOdd() {
      return Math.floor(this.movie.vote_average) % 2;
    },
  },
};
</script>
<style lang="scss" scoped>
.movies li {
  border: 1px solid red;
}
.series li {
  border: 1px solid green;
}
li {
  height: 350px;
  .inner {
    perspective: 1000px;
    height: 100%;
    width: 100%;
    position: relative;
    &:hover {
      .front {
        transform: rotateY(-0.5turn);
      }
      .back {
        transform: rotateY(0turn);
      }
    }
  }
  .back,
  .front {
    transition: 0.8s;
    width: 100%;
    height: 100%;
    position: absolute;
    backface-visibility: hidden;
  }
  .front {
    img {
      width: 100%;
      height: 100%;
    }
  }
  .back {
    transform: rotateY(180deg);
  }
  h2,
  p {
    text-align: center;
  }
  p {
    font-size: 1.5rem;
    &.star {
      color: goldenrod;
    }
    &.description {
      font-size: 1rem;
    }
  }
  .flag {
    width: 30px;
    height: auto;
    border: 1px solid black;
  }
}
</style>
