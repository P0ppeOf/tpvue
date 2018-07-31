<template>
    <div class="header">
        <h1>
            Movies
        </h1>
    </div>
</template>

<script>
export default {
     name: 'Header',
  props: {
    msg: String
  }
};
</script>

<style lang ="less" scoped>
.header {
  background-image: url("/metol.jpg");
  background-repeat: no-repeat;
  background-size: 100%;
  border-radius: 0px 0px 20px 20px;
  border: 5px solid;
  border-color: black;
  box-shadow: 0px 20px 15px black;

h1 {
    color: black;
    text-align: center;
    font-family: Verdana, sans-serif;
}}

@media screen and (max-width : 1120px) {  

    .header{
        height:65px;
    }        
}

@media screen and (max-width : 520px)
{    
    .header {
        height:50px;
                h1 {
                    font-size: 1em;
                }
        }
}
</style>
