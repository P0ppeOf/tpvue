<template>
  <div id="app">
    <Header/>  
    <div class = "swipContent">
  <div class = "swip" :class="{ bouge: moviesState.selectedMovie }">
    <MovieList>
    </MovieList>
    <Popup v-if="moviesState.selectedMovie"/>
     </div>
  </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import MovieList from "./components/MovieList.vue";
import Popup from "./components/Popup.vue";
import { moviesState } from "./states/movies-state";

//import Loader from './components/Loader.vue'

export default {
  name: "app",
  components: {
    Header,
    Popup,
    MovieList
    // Loader
  },

  data() {
    return {
      moviesState
    };
  }
};
</script>

<style lang="less">
@import "~normalize.css";

#app {
  background-color: #17181b;
  font-family: Verdana, sans-serif;
  height: 100vh;
  display: flex;
  flex-direction: column;
}

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
