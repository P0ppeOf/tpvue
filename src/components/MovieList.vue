<template>
<div class = "movieList">
    <Movie
    v-for="(movie, index) in movies" :key="index" :movie="movie" :selectMovie="selectMovie">
    </Movie>
<Movie :movie="movies[1]" :selectMovie="selectMovie" ></Movie>

<Popup
v-if="selectedMovie"
:movie="selectedMovie"
:selectMovie="selectMovie"
/>
</div>
</template>

<script>
import Movie from './Movie.vue'
import Popup from './Popup.vue'

export default {
  name: 'MovieList',
  components: {
    Movie,
    Popup
  },

  methods: {
    selectMovie (movie) {
      this.selectedMovie = movie
    },

    closeDetail () {
      this.selectedMovie = null
    }
  },

  data () {
    return {
      selectedMovie: null,
      movies: [] // on créé un tableau
      /* movies: [
         Tableau de films
       { title: "Matrix", url: "matrix.jpg" },
        { title: "Dead Man", url: "dead.jpg" },
        { title: "Jurassic Park", url: "jpark.jpg" }
      ] */
    }
  },

  async created () {
    try {
      let response = await fetch('movies.json')
      this.movies = await response.json() // ici on rempli le tableau precedemment créé avec le json
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
