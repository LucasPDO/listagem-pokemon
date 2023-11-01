<template>
  <h1>Listando 15 Pokemons</h1>
    <p>Consumindo atraves da api de pokemon</p>
  <table id="customers">
      <tr>
       <td>Nome</td> 
      </tr>
      <tr v-for="item in pokemons" :key="item" >
       {{  item }}
      </tr>      
    
  </table>
</template>

<script>
import axios from "axios";

export default {
  name: 'ListPokemons',

 data() {
  return {
    pokemons: ''
  }
  
 },

methods: {
  listarPokemon() {
    axios 
    .get('https://pokeapi.co/api/v2/pokemon?limit=15&offset=0')
    .then(response => {
      this.pokemons = response.data.results
      .map(item => item.name);
    })
    .catch(error => {
      console.error(error);
    }) 

    
  } 
},
created() {
  this.listarPokemon();
}
}
</script>

<style scoped>
#customers {
  font-family: Arial, Helvetica, sans-serif;
  border-collapse: collapse;
  width: 50%;
  margin: 0 auto;
}

#customers td, #customers th {
  border: 1px solid #ddd;
  padding: 8px;
}

#customers tr:nth-child(even){background-color: #f2f2f2;}

#customers tr:hover {background-color: #ddd;}

#customers th {
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: left;
  background-color: #04AA6D;
  color: white;
}
</style>
