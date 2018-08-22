<template>
<div class="background" @click="backClick($event)" >
    <div class="popup">
      <h4>{{ moviesState.selectedMovie.title }}</h4>
      <div class ="row">
      <img :src="moviesState.selectedMovie.url"/>
      <p>{{ moviesState.selectedMovie.synopsys }}</p>
      </div>
      <button type="button" @click="closePopup()">Close</button>
    </div>
</div>
</template>

<script>
import { moviesState } from "../states/movies-state";

export default {
  name: "Popup",
  
  data() {
    return {
      moviesState
    }
  },

 created () {
      document.addEventListener('keydown', this.escapeKeyListener)
    },
  
    beforeDestroy () {
      document.removeEventListener('keydown', this.escapeKeyListener)
    },

  methods: {
     backClick(event)
 {
   console.log(event)

    if (event.target.className === "background" )
    {
      this.closePopup()
    } 
 },
    closePopup() {
      this.moviesState.selectedMovie = null
    },

  escapeKeyListener (event) {
    if (event.key === 'Escape') {
      this.closePopup()
    }
  }
}
};
</script>

<style lang="less" >


.background { 

  //position: fixed;
  background-color: rgba(255, 255, 255, 0.6);

  width: 100vw;
  position: absolute;
  top: 0px;
  left: 100vw;
  bottom: 0px;
/*   top: 0px;
  left: 0px; */


  .popup {
    width: 50vw;
    margin-left: 25vw;
    margin-top: 20vh;
    position: center;
    background: black;
    color: white;
    box-shadow: 0px 10px 8px black;
    border-radius: 10px;
    padding-top: 10px;
   

  }


  button {
    background: #2b71d8;
    width: 50vw;
    margin-top: 20px;
    color: white;
    border-radius: 0px 0px 10px 10px;
  }

  .row {
    display: flex;
    flex: row;
  }

  img {
    width: 225px;
    height: 320px;
    border-radius: 10px;
    box-shadow: 0px 10px 8px black;
    transition: transform 0.5s, border 0.5s;
    box-sizing: border-box;
    margin-left: 20px;
    margin-right: 20px;
  }
  p {
    margin-right: 20px;
    flex-wrap: wrap;
  }
  h4 {
    font-size: 20px;
    margin-left: 20px;
  }
}
</style>
