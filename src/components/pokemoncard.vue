<template>
    <div class="pokemon-card">
      <img :src="pokemonImage" :alt="pokemon.name" />
      <h3>{{ pokemon.name }}</h3>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      pokemon: {
        type: Object,
        required: true
      },
      id: {
        type: Number,
        required: true
      }
    },
    computed: {
      pokemonImage() {
        return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${this.id}.png`;
      }
    }
  };
  </script>
  
  <style scoped>
  .pokemon-card {
    display: flex;
    flex-direction: column;
    align-items: center;
    border: 1px solid #ddd;
    border-radius: 10px;
    padding: 10px;
    text-align: center;
    box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);
    background-color: #f8f8f8;
  }
  
  .pokemon-card img {
    width: 100px;
    height: 100px;
  }
  
  .pokemon-card h3 {
    margin: 10px 0 0;
    text-transform: capitalize;
  }
  </style>
  