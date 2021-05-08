<template>
  <div id="app">
    <div v-for="pokemon in pokemons" :key="pokemon.name">
      <Pokemon :name="pokemon.name" :url="pokemon.url"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Pokemon from './components/Pokemon';

export default {
  name: 'App',
  data(){
    return{
      pokemons: []
    }
  },
  created: function(){
    axios.get("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0").then(res =>{
      this.pokemons = res.data.results;
    }).catch(err => {
      console.log(err);
    });

  },
  components:{
    Pokemon
  }
}
</script>

<style>
#app p{
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
