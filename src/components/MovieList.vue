<template>
<div class = "movieList">
    <Movie
    v-for="(movie, index) in movies" 
    :key="index"       
    :title="movie.title" 
    :img="getImgUrl(movie)"
    > 
    </Movie>

<Movie :title="movies[0].title" :img="'/imgs/' + movies[0].url" />  <!-- Pour un film du tableau dans data, pas json -->

</div>
</template>

<script>
import Movie from "./Movie.vue";

export default {
  name: "MovieList",
  components: {
    Movie
  },


  data() {
      return {
          movies: [] //on créé un tableau
     /* movies: [
         Tableau de films
       { title: "Matrix", url: "matrix.jpg" },
        { title: "Dead Man", url: "dead.jpg" },
        { title: "Jurassic Park", url: "jpark.jpg" }
      ]*/
    }
  },
    async created() {
        //fetch
        
        try {
            let response = await fetch('movies.json')
            this.movies = await response.json() //ici on rempli le tableau precedemment créé avec le json

        } catch(error) {
            console.log(error)
        }
    },
    methods: {
        getImgUrl (movie) {
            return `/imgs/${movie.url}`
        }
    }


};
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
