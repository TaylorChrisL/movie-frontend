<script>
import axios from "axios";
export default {
  data: function () {
    return {
      movie: {},
    };
  },
  created: function () {
    axios.get("/movies/" + this.$route.params.id + ".json").then((response) => {
      this.movie = response.data;
    });
  },
  methods: {
    destroyMovie: function () {
      axios.delete("/movies/" + this.$route.params.id + ".json").then((response) => {
        console.log("IT GONE!", response.data);
        this.$router.push("/movies");
      });
    },
  },
};
</script>

<template>
  <div class="movies-show">
    <div class="container">
      <h1>{{ movie.title }}</h1>
      <p>
        {{ movie.plot }}
      </p>
      <router-link to="/movies">Return to All movies</router-link>
      |
      <router-link v-bind:to="`/movies/${movie.id}/edit`">Edit this Movie</router-link>
      <div>
        <button v-on:click="destroyMovie()">Delete this Movie</button>
      </div>
    </div>
  </div>
</template>

<style>
img {
  max-width: 200px;
  max-height: 300px;
}
</style>
