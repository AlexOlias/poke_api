<template>
  <div id="app">
    <h1>Pokémon List</h1>
    <div class="pokemon-list">
      <PokemonCard
        v-for="(pokemon, index) in pokemons"
        :key="pokemon.name"
        :pokemon="pokemon"
        :id="index + 1"
      />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import PokemonCard from '@/components/pokemoncard.vue';

export default {
  components: {
    PokemonCard
  },
  data() {
    return {
      pokemons: []
    };
  },
  created() {
    this.fetchPokemons();
  },
  methods: {
    async fetchPokemons() {
      try {
        const response = await axios.get('https://pokeapi.co/api/v2/pokemon/?offset=0&limit=151');
        this.pokemons = response.data.results;
      } catch (error) {
        console.error('Error fetching Pokémon:', error);
      }
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
}

.pokemon-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
  gap: 20px;
  padding: 20px;
  max-width: 1000px;
  margin: auto;
}
</style>
