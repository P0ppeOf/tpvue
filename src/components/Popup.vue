<template>
<div class="background">
    <div class="popup">
      <h4>{{ movie.title }}</h4>
      <img :src= "movie.url">
      <p>{{ movie.synopsys }}</p>
      <button type="button" @click="closeDetail()">Close</button>
    </div>
</div>
</template>

<script>

export default {
  name: "Popup",
  props: {
    movie : Object,
    closeDetail: Function
  }
};
</script>

<style lang="less" >
.background {
  position: fixed;
  background-color: rgba(255, 255, 255, 0.6);
  height: 100vh;
  width: 100vw;
  top: 0;
  left: 0;

.popup {
  width: 50vw;
  margin-left: 25vw;
  margin-top: 20vh;
  position: center;
  background: black;
  color: white;
  box-shadow: 0px 10px 8px black;
  border-radius: 10px;
}

button {
    background : #2b71d8;
    width :50vw;
    margin-top : 10px;
    color :white;
    border-radius: 0px 0px 10px 10px;
}

img {
    width: 225px;
    height: 320px;
    border-radius: 10px;
    box-shadow: 0px 10px 8px black;
    transition: transform 0.5s, border 0.5s;
    box-sizing: border-box;
    margin-left : 20px;
}
}
</style>