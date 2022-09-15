<template>
 <div class="pokemon-container">
  <img :src="pokemon.image" alt="Pokemon image">
  <div class="pokemon-info">
    <h4>{{pokemon.name}}</h4>
    <p>{{pokemon.classfication}}</p>
  </div>
 </div>
</template>

<script>
export default {
  props: ['pokemon']

}
</script>

<style scoped>
.pokemon-container{
  border: 1px solid black;
  display: flex;
  align-items: center;
  margin: 10px;
  padding: 10px;
  cursor: pointer;
}
.pokemon-container img{
  width: 50px;
}

</style>