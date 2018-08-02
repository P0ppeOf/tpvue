ça y en a global state
movie-state.js

export const moviesState = {
    movies: null,
    selectedMovie: null
}

// movie.vue

<template>
    <div class="affiche" @click="selectMovie()">
    <img :src="getImgUrl()"/>
    <h4>{{ movie.title }}</h4>
    </div>
</template>

<script>
import { moviesState } from "../states/movies-state";

export default {
  name: "Movie",
  props: {
    movie: Object
  },
  data() {
    return {
      moviesState
    }
  },

  methods: {
    getImgUrl() {
      return `/imgs/${this.movie.url}`;
    },
    /* selectMovie () {
      this.$emit('clickOnMovie', this.movie)
    } */
    selectMovie() {
      this.moviesState.selectedMovie = this.movie
    }
  }
};
</script>


// movie list.vue

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
</div>
</template>

<script>
import Movie from './Movie.vue'
import Popup from './Popup.vue'
import { moviesState } from '../states/movies-state'

export default {
  name: 'MovieList',
  components: {
    Movie,
    Popup
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
      moviesState 
      //1 on imorte le fichier pour init, ça remplace en dessous
      /* selectedMovie: null,
      movies: [] */
    }
  },

  async created () {
    try {
      let response = await fetch('movies.json')
      this.moviesState.movies = await response.json() // ici on rempli le tableau precedemment créé avec le json
 } catch (error) {
      console.log(error)
    }
  }
}
</script>