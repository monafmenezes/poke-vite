<script setup>
import { onMounted, reactive, ref, computed } from 'vue'
import ListPokemons from '../components/ListPokemons.vue';
import CardPokemonSelected from '../components/CardPokemonSelected.vue'

let pokemons = reactive(ref())
let baseUrl = ref('https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/')
let searchPokemonField = ref('')
let loading = ref(false)

onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0").then((res) => res.json())
    .then(res => {
      pokemons.value = res.results
    })
})

const pokemonsFiltered = computed(() => {
  if (pokemons.value && searchPokemonField.value) {
    return pokemons.value.filter(pokemon => {
      return pokemon.name.toLowerCase().includes(searchPokemonField.value.toLowerCase())
    })
  }  
  return pokemons.value
})

let pokemonSelected = reactive(ref())
const selectPokemon = async (pokemon) => {
  loading.value = true
  await fetch(pokemon.url)
  .then(res => res.json())
  .then(res => {
    pokemonSelected.value = res
    pokemonSelected.value.name = pokemon.name
  })
  .catch(err => alert(err))
  .finally(() => loading.value = false)
}

</script>

<template>
  <main>
    <div class="container text-center text-body-secondary">
      <div class="row mt-4">

        <div v-if="pokemonSelected" class="mt-4 col-sm-12 col-md-6">
          <cardPokemonSelected 
            :pokemon="pokemonSelected"
            :loading="loading"
          />
        </div>

        <div 
        :class="pokemonSelected ? 'col-md-6' : 'col-md-12'"
        class="card cardList mt-4 col-sm-12 col-md-6">
          <div class="card-body row">
            <div class="mb-3">
              <label 
              hidden 
              for="searchPokemonField" 
              class="form-label"
              >Pesquisar...</label>
              <input 
              v-model="searchPokemonField"
              type="text" 
              class="form-control" 
              id="searchPokemonField" 
              placeholder="Pesquisar"
              >
            </div>
            <ListPokemons 
            v-for="pokemon in pokemonsFiltered" 
            :key="pokemon.name" 
            :name="pokemon.name"
            :url="baseUrl + pokemon.url.split('/')[6] + '.svg'" 
            @click="selectPokemon(pokemon)"/>
          </div>
        </div>

      </div>
      
    </div>
  </main>
</template>

<style scoped>
.cardList {
  max-height: 75vh;
  overflow-y: scroll;
  overflow-x: hidden;
}
</style>