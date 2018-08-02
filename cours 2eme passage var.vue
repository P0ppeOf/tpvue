//Movie 

<template>
    <div class="affiche" @click="selectMovie(movie)">
    <img :src="getImgUrl()"/>
    <h4>{{ movie.title }}</h4>
    </div>
</template>

<script>
export default {
  name: 'Movie',
  props: {
    movie: Object
  },
  methods: {
    getImgUrl () {
      return `/imgs/${this.movie.url}`
    },
    selectMovie () {
      this.$emit('clickOnMovie', this.movie)
    }
  }
}
</script>


//Movie list

<template>
<div class = "movieList">
    <Movie
    v-for="(movie, index) in movies" 
    :key="index" 
    :movie="movie" 
    @clickOnMovie="selectMovie">
    </Movie>
<Movie :movie="movies[1]" @clickOnMovie="selectMovie" ></Movie>

<Popup
v-if="selectedMovie"
:movie="selectedMovie"
@closeOnClick="closeDetail"

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
