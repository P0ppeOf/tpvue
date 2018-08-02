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

<style lang="less" scoped>
div.affiche {
  width: 225px;
  color: white;
  text-align: center;
  margin-top: 30px;
  margin-left: 30px;
  margin-right: 30px;

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
