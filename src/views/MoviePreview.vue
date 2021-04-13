<template>
  <div class="container movies-wrapper">
    <div class="row">
      <div class="col-lg-4">
        <div class="item-img">
          <img :src="movie.imgSrc" alt="" />
        </div>
      </div>
      <div class="col-lg-8">
        <div class="mov-i">
          <span>{{ movie.movieDate }}</span>
          <span id="mov-t">{{ movie.movieCat }}</span>
          <span id="mov-d">{{ movie.movieQuality }}</span>
          <h5>
            <a>{{ movie.movieName }}</a>
          </h5>
          <p id="m-desc">{{ movie.movieDesc }}</p>
          <div>
            <button @click="showModel = true" id="update-movie">Update</button>
            <button id="remove-movie" @click="removeMovie">Remove</button>
          </div>
        </div>
      </div>
    </div>
  </div>

  <model v-if="showModel" @close="showModel = !showModel">
    <template v-slot:header>
      <h3>Update Movie</h3>
    </template>

    <template v-slot:body>
      <form @submit.prevent="updateMovie" ref="movieForm" id="movie-form">
        <p>Please Fill The Data Below</p>
        <input
          v-model="movie.movieName"
          type="text"
          required
          placeholder="MovieName"
        />
        <input
          v-model="movie.imgSrc"
          type="text"
          required
          placeholder="Movie Poster Url"
        />
        <input
          v-model="movie.movieDate"
          type="text"
          required
          placeholder="MovieDate"
        />
        <input
          v-model="movie.movieCat"
          type="text"
          required
          placeholder="MovieCat"
        />
        <input
          v-model="movie.movieQuality"
          type="text"
          required
          placeholder="MovieQuality"
        />
        <input
          v-model="movie.seasons"
          type="text"
          required
          placeholder="Seasons"
        />

        <textarea
          v-model="movie.movieDesc"
          rows="6"
          required
          placeholder="Movie Description"
        ></textarea>
      </form>
    </template>

    <template v-slot:footer>
      <button id="add-movie" @click="$refs.movieForm.requestSubmit()">
        Update
      </button>
    </template>
  </model>
</template>

<script>
import Model from "../components/Model.vue";
export default {
  data() {
    return {
      showModel: false,
      movie: {},
    };
  },
  methods: {
    removeMovie() {
      this.$store.dispatch("removeMovie", parseInt(this.id));
      this.$router.push("/");
    },
    updateMovie() {
      this.$store.dispatch("updateMovie", this.movie);
      this.showModel = false;
      this.$router.push("/");
    },
  },
  created() {
    this.movie = this.$store.getters.getMovieById(parseInt(this.id));
  },
  props: {
    id: {
      type: Number,
      default: null,
    },
  },
  components: {
    Model,
  },
};
</script>

<style lang="scss">
.movies-wrapper {
  margin-top: 70px;
  .item-img {
    width: 100%;
    img {
      width: 100%;
      height: 100%;
    }
  }
  .mov-i {
    padding-top: 10px;

    span {
      font-size: 0.8rem;
      font-weight: bold;
    }
    #mov-t {
      color: red;
      font-weight: bold;
      padding-left: 5%;
    }
    #mov-d {
      color: #d4d4d4;
      border: 1px solid #a3a3a8;
      padding: 1px 2px;
      font-size: 0.6rem;
      font-weight: bold;
      margin-left: 25px;
    }
    #m-desc {
      background: black;
      color: #fff;
      padding: 8px 20px;
      text-transform: uppercase;
      font-weight: 700;
      &:hover {
        background: rgb(221, 32, 32);
        color: #fff;
        transition: 0.5s all ease;
      }
    }
    #update-movie {
      border: 0;
      padding: 8px 15px;
      background: green;
      font-weight: 600;
      text-transform: uppercase;
      color: #fff;
      margin-right: 25px;
    }
    #remove-movie {
      border: 0;
      padding: 8px 15px;
      background: red;
      font-weight: 600;
      text-transform: uppercase;
      color: #fff;
      margin-left: 25px;
    }
    h5 {
      a {
        color: #333;
        font-weight: bold;
        font-size: 1rem;
      }
    }
    #btnaddfav {
      text-transform: uppercase;
      font-size: 0.9rem;
      font-weight: bold;
      background: #333;
      color: #fff;
      padding: 15px 35px;
      border: 1px solid #333;
      &:hover {
        background: red;
        transition: 0.6s all ease;
        border: 1px solid red;
      }
    }
  }
}
</style>
