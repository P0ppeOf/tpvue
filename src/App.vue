<template>
  <div id="app">
    <Header/>  
<!--   <button>+</button> -->
 
    <router-link to="/Formulaire">
  <button class="plusBout" v-if="moviesState.bouton.value">+</button>
</router-link>
    <router-view>
<!--  <MovieListPage/>  -->
    </router-view>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
//import MovieList from "./components/MovieList.vue";
//import MovieListPage from "./components/MovieListPage.vue";
//import Popup from "./components/Popup.vue";
import { moviesState } from "./states/movies-state";

//import Loader from './components/Loader.vue'

export default {
  name: "app",
  components: {
    Header,
   // Popup,
   // MovieList,
   //MovieListPage
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

button.plusBout {
  height : 100px;
  width : 100px;
  top:80%;
  right:10%;
  position:absolute;
  z-index: 9999;
  border-radius: 100px;
  background-color: #2b71d8 ;
  color: white;
  font-size: 300%;
  font-weight: bold;
  border:0px;
  box-shadow: 4px 4px 4px black;
}
</style>
