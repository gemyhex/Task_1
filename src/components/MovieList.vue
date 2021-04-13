<template>
  <div class="container movies-wrapper">
    <div class="row">
      <div class="col-lg-12">
        <button @click="showModel = true" id="add-movie">(+) add movie</button>
      </div>
    </div>
    <div class="row shuffle-items">
      <movie v-for="movie in movies" :key="movie.id" :movie="movie"></movie>
    </div>

    <model v-if="showModel" @close="showModel = !showModel">
      <template v-slot:header>
        <h3>Create New Movie</h3>
      </template>

      <template v-slot:body>
        <form @submit.prevent="addMovie" ref="movieForm" id="movie-form">
          <p>Please Fill The Data Below</p>
          <input
            v-model="movieForm.movieName"
            type="text"
            required
            placeholder="MovieName"
          />
          <input
            v-model="movieForm.imgSrc"
            type="text"
            required
            placeholder="Movie Poster Url"
          />
          <input
            v-model="movieForm.movieDate"
            type="text"
            required
            placeholder="MovieDate"
          />
          <input
            v-model="movieForm.movieCat"
            type="text"
            required
            placeholder="MovieCat"
          />
          <input
            v-model="movieForm.movieQuality"
            type="text"
            required
            placeholder="MovieQuality"
          />
          <input
            v-model="movieForm.seasons"
            type="text"
            required
            placeholder="Seasons"
          />

          <textarea
            v-model="movieForm.movieDesc"
            rows="6"
            required
            placeholder="Movie Description"
          ></textarea>
        </form>
      </template>

      <template v-slot:footer>
        <button id="add-movie" @click="$refs.movieForm.requestSubmit()">
          Add
        </button>
      </template>
    </model>
  </div>
</template>

<script>
import Movie from "./Movie.vue";
import Model from "./Model.vue";
export default {
  data() {
    return {
      showModel: false,
      movies: [],
      movieForm: {
        movieName: "",
        imgSrc: "",
        movieDate: "",
        movieCat: "",
        movieQuality: "",
        movieDesc: "",
        seasons: "",
      },
    };
  },
  methods: {
    addMovie(e) {
      e.preventDefault();
      this.$store.dispatch("addMovie", this.movieForm);
      this.showModel = false;
    },
  },
  created() {
    this.movies = this.$store.getters.getMovies;
  },
  components: {
    Movie,
    Model,
  },
};
</script>

<style lang="scss" scoped>
.movies-wrapper {
  position: relative;
  background: #fff;
  padding: 0;
  padding-bottom: 400px;
  margin-top: 70px;
  #add-movie {
    float: right;
    border: 1px solid black;
    padding: 8px 15px;
    background: red;
    font-weight: 600;
    text-transform: uppercase;
    color: #fff;
    margin-left: 25px;
  }

  .shuffle-items {
    transition: all 1s ease;
  }
}
</style>
