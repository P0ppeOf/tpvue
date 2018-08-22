<template>
    <div class="affiche" >
    <img :src="movie.url" @click="selectMovie()"/>
    <LoaderMovie
  v-if="validPop.value"
  />
    <h4>{{ movie.title }}</h4>
    </div>
</template>

<script>
import { moviesState } from "../states/movies-state";
import LoaderMovie from './LoaderMovie.vue'

export default {
  name: "Movie",
  components: {
    LoaderMovie
  },
  props: {
    movie: Object
  },
  data() {
    return {
      moviesState,
       validPop: {
        value : false
      } 
    }
  },

  methods: {

    /* selectMovie () {
      this.$emit('clickOnMovie', this.movie)
    } */

     async selectMovie() {
      try {
        this.validPop.value = true
     let ligneTab = await fetch("http://localhost:5000/Movies/" + this.movie.id)
      const mov = await ligneTab.json() 
      this.moviesState.selectedMovie = mov
      this.validPop.value = false
    } catch(error) {
      console.log("error")
    }
  } 
  }
};
</script>

<style lang="less" scoped>
div.affiche {
  width: 225px;
  height: 400px;
  color: white;
  text-align: center;
  margin-top: 30px;
  margin-left: 30px;
  margin-right: 30px;
  position: relative;
  img {
    width: 225px;
    height: 320px;
    border-radius: 10px;
    box-shadow: 0px 10px 8px black;
    transition: transform 0.5s, border 0.5s;
    box-sizing: border-box;

    &:hover {
      border: 7px solid;
      border-color: #2b71d8;
      transform: scale(1.2);
    }
  }

  h4 {
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
}

@media screen and (max-width: 1120px) {
  div.affiche {
    width: 140px;
    color: white;
    text-align: center;
    margin-top: 20px;
    margin-left: 10px;
    margin-right: 10px;
    img {
      width: 140px;
      height: 200px;
      border-radius: 10px;
      box-shadow: 0px 5px 4px black;
    }
  }
}
@media screen and (max-width: 520px) {
  div.affiche {
    width: 75px;
    color: white;
    text-align: center;
    margin-top: 20px;
    margin-left: 10px;
    margin-right: 10px;
    img {
      width: 75px;
      height: 110px;
      border-radius: 10px;
      box-shadow: 0px 5px 4px black;
    }
    h4 {
      font-size: 0.8em;
    }
  }
}
</style>
