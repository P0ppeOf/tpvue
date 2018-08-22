<template>
    <div class="form" >
    <p> Ajouter un film</p>
    <form 
    @submit.prevent="checkForm"
    >
      Titre :
      <input v-model="titre" placeholder="Title"><br>
      Url de l'image :
     <input v-model="imgURL" placeholder="Image URL">
      Synopsis :
       <textarea v-model="synopsis" placeholder="Synopsis"></textarea><br>
      <input class="bouton" type="submit" value="Moult">
    </form>
  <LoaderMovie
  v-if="validPop.value"
  />
    </div>
</template>

<script>
import { moviesState } from "../states/movies-state";
import LoaderMovie from './LoaderMovie.vue'

export default {
  name: "Formulaire",
components: {
    LoaderMovie
  },
  data() {
    return {
      moviesState,
      validPop: {
        value : false
      } ,
      titre: null,
      imgURL: null,
      synopsis: null
    };
  },

  methods:{
    async checkForm(e) {
      try {
      this.validPop.value = true
     await fetch ("http://localhost:5000/form", {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify(
        {titre:this.titre,
        imgURL:this.imgURL,
        synopsis:this.synopsis
        }
        )
      })
      }
      catch (error) {
      console.log(error);
    }
     this.validPop.value = false
          this.$router.go(-1)
    }
    },

  created() {
    moviesState.bouton.value = false;
  }
};
</script>

<style scoped>
div.form {
  position: relative;
  top: 20%;
  left: 38%;
  height: 50%;
  width: 24%;
  background-color: white;
  border-radius: 6%;
  border: 2px solid;
  border-color: blue;
  box-shadow: 0px 10px 8px black;
}

p {
  /* border: 0px 0px 1px 0px solid;
  border-color: blue; */
  text-align: center;
  font-size: 200%;
  margin-top: 5%;
}

 input.bouton {
margin-top: 30px;
    /*  bottom: 0px; */
    background: #2b71d8;
    width: 100%;
    margin-top: 20px;
    color: white;
    border-radius: 0px 0px 6px 6px;
  }

  form {
    display :flex;
    flex-direction: column;
    flex-grow: 1;
  }
</style>


