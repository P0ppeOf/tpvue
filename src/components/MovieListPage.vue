<template>
 
    <div class = "swipContent">
  <div class = "swip" :class="{ bouge: moviesState.selectedMovie }">
    <MovieList/>
    <Popup v-if="moviesState.selectedMovie"/>
     </div>
  </div>
</template>

<script>
import MovieList from "./MovieList.vue";
import Popup from "./Popup.vue";
import { moviesState } from "../states/movies-state";

//import Loader from './components/Loader.vue'

export default {
  name: "MovieListPage",
  components: {
    Popup,
    MovieList,
    // Loader
  },

  data() {
    return {
      moviesState
    };
  },

  created() {
    moviesState.bouton.value = true;
}
};
</script>

<style lang="less">

.swipContent {
  position: relative;
  width: 100vw;
  display: flex;
  flex-grow: 1;
  overflow: hidden;
  .swip {
    position: absolute;
    top: 0px;
    left: 0px;
    bottom: 0px;
    width: 200vw;
    display: flex;
    flex-direction: row;
    transition: transform 1s;
    &.bouge {
      transform: translate(-100vw);
    }
  }
}
</style>
