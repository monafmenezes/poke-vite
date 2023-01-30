<script setup>
const pokemon = defineProps(['name', 'url'])
</script>

<template>
    <div class="col-xs-12 col-md-6 col-lg-4">
        <div class="card mb-3 p-3 cardListPokemon">
            <h5 class="text-center">{{ pokemon.name }}</h5>
            <img 
            :src="url" 
            :alt="pokemon.name"
            height="100" 
            class="card-img-top" 
            />
        </div>
    </div>
</template>

<style scoped>
.cardListPokemon {
  background: rgb(121, 63, 251);
  background: radial-gradient(circle, rgba(121, 63, 251, 0.43886462882096067) 0%, rgba(70, 252, 252, 0.5786026200873362) 100%);
  cursor: pointer;
}

.cardListPokemon:hover {
    filter: brightness(0.9);
}

.cardListPokemon img:hover {
    scale: 103%;
}
</style>