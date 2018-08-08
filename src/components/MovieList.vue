<template>
<div class = "movieList">
  
    <Movie
    v-for="(movie, index) in moviesState.movies" 
    :key="index" 
    :movie="movie" 
    >
    </Movie>


<Popup
v-if="moviesState.selectedMovie"
/>
  <Loader
  v-if="validPop.value"
  />
</div>
</template>

<script>
import Movie from './Movie.vue'
import Popup from './Popup.vue'
import Loader from './Loader.vue'
import { moviesState } from '../states/movies-state'

export default {
  name: 'MovieList',
  components: {
    Movie,
    Popup,
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

  data () {
    return {
      moviesState,
      validPop: {
        value : false
      } 
      //1 on imorte le fichier pour init, ça remplace en dessous
      /* selectedMovie: null,
      movies: [] */
    }
  },

  async created () {
    try {
      this.validPop.value = true
      let response = await fetch("http://localhost:5000/Movies")
      this.moviesState.movies = await response.json() // ici on rempli le tableau precedemment créé avec le json
      this.validPop.value = false
 } catch (error) {
      console.log(error)
    }
  }
}
</script>

<style scoped>
div.movieList {
  display: flex;
  justify-content: space-around;
  flex-direction: row;
  flex-wrap: wrap;
  overflow: scroll;
  flex-grow: 1;
  margin-left: 30px;
  margin-right: 30px;
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
