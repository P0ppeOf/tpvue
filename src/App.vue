<template>
  <div id="app">
    <Header/>  
    <MovieList>
    </MovieList>
  
  </div>
</template>

<script>
import Header from './components/Header.vue'
import MovieList from './components/MovieList.vue'
//import Loader from './components/Loader.vue'

export default {
  name: 'app',
  components: {
    Header,
    MovieList
   // Loader
  }
}
</script>

<style lang="less">
@import '~normalize.css';

#app {
   background-color: #17181b;
    font-family: Verdana, sans-serif;
   height : 100vh;
    display:flex;
    flex-direction : column;
}
</style>
