<template>
  <div class="home-container">
    <img
      :src="pokemon.image"
      alt="Pokemon image"
    />

    <div class="select-container">
      <label for="pokemon-select">Select Type:</label>
      <select
        name="pokemon-type"
        id="pokemon-type"
        v-model="selectedPokemon"
        @change="filterPokemon($event)"
      >
        <option disabled value="Please">Please select one</option>
        <option v-for="pokemon in pokemonTypes" :key="pokemon" :value="pokemon">
          {{ pokemon }}
        </option>
      </select>
    </div>

    <div class="container">
      <div
        class="pokemons-container"
        v-for="pokemon in pokemons"
        :key="pokemon"
      >
        <app-pokemon :pokemon="pokemon" @click="showModal(pokemon)" />
      </div>
    </div>

    <div class="button-container">
      <hr />
      <button @click="showModal">Button</button>
    </div>
  </div>

  <div class="modal-container">
    <app-modal :pokemon="pokemon" v-show="isModalVisible" @close="closeModal" />
     
   
  </div>
</template>

<script>
import PokemonData from "../assets/pokemon.json";
import AppPokemon from "./AppPokemon.vue";
import AppModal from "./AppModal.vue";

export default {
  data() {
    return {
      pokemonObj: {},
      pokemonTypes: [],
      selectedPokemon: "grass",
      grassPokemons: [],
      waterPokemons: [],
      firePokemons: [],
      pokemons: [],
      isModalVisible: false,
      pokemon: {},
    };
  },
  components: {
    AppPokemon,
    AppModal,
  },
  created() {
    this.pokemonObj = PokemonData;
    this.pokemon.image = 'https://img.pokemondb.net/sprites/x-y/normal/bulbasaur.png'
    for (const [key, value] of Object.entries(this.pokemonObj)) {
      this.pokemonTypes.push(key);
      if (key === "grass") {
        this.pokemons = value;
      } else if (key === "water") {
        this.pokemons = value;
      } else if (key === "fire") {
        this.pokemons = value;
      }
    }
  },
  methods: {
    filterPokemon() {
      for (const [key, value] of Object.entries(this.pokemonObj)) {
        if (this.selectedPokemon === key) {
          this.pokemons = value;
        }
      }
    },
    showModal(pokemon) {
      this.isModalVisible = true;
      this.pokemon = pokemon;
    },
    closeModal() {
      this.isModalVisible = false;
    },
  },
};
</script>

<style scoped>
.home-container {
  border: 2px solid black;
  margin: 10vh auto;
  width: 90%;
  max-width: 400px;
  border-radius: 20px;
  padding: 10px;
}
.home-container img {
  display: block;
  margin: 0 auto;
  width: 50%;
  max-width: 300px;
}
.home-container .select-container {
  margin: 0 auto;
  width: 100%;
  display: block;
  padding: 5px;
}
.home-container .select-container label {
  display: block;
  width: 50%;
  margin: 0 auto;
  font-size: 15px;
}
.home-container .select-container select {
  margin: 0 auto;
  width: 50%;
  display: block;
  padding: 5px;
}
.container {
  overflow-y: auto;
  height: 40vh;
}
.button-container button {
  border: none;
  padding: 10px 25px;
  width: 100%;
  margin: 10px auto;
  background-color: #082284;
  cursor: pointer;
  color: #ffffff;
  font-weight: 800;
  text-transform: uppercase;
}
</style>