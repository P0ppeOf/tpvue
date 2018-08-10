<template>

<div class = "movieList">
    <Movie
    v-for="(movie, index) in moviesState.movies" 
    :key="index" 
    :movie="movie" 
    >
    </Movie>
    <Loader
  v-if="validPop.value"
  />
</div>

 
  

</template>

<script>
import Movie from "./Movie.vue";

import Loader from "./Loader.vue";
import { moviesState } from "../states/movies-state";

export default {
  name: "MovieList",
  components: {
    Movie,
    Loader
  },

  /* on supprime les methodes parce que les var glob sont dans le state global
   methods: {
    selectMovie (movie) {
      this.selectedMovie = movie
    },

    closeDetail () {
      this.selectedMovie = null
    }
  }, */

  data() {
    return {
      moviesState,
      validPop: {
        value: false
      }
      //1 on imorte le fichier pour init, ça remplace en dessous
      /* selectedMovie: null,
      movies: [] */
    };
  },

  async created() {
    try {
      this.validPop.value = true;
      let response = await fetch("http://localhost:5000/Movies");
      this.moviesState.movies = await response.json(); // ici on rempli le tableau precedemment créé avec le json
      this.validPop.value = false;
    } catch (error) {
      console.log(error);
    }
  }
};
</script>

<style scoped>
div.movieList {
  position: absolute;
  top: 0px;
  left: 0px;
  bottom: 0;
  display: flex;
  justify-content: space-around;
  flex-direction: row;
  flex-wrap: wrap;
  overflow: scroll;
  flex-grow: 1;
  /* margin-left: 30px;
  margin-right: 30px; */
  width: 100vw;
}


@media screen and (max-width: 1120px) {
  div.movieList {
    margin-left: 20px;
    margin-right: 20px;
  }
}
@media screen and (max-width: 520px) {
  div.movieList {
    margin-left: 20px;
    margin-right: 20px;
  }
}
</style>
