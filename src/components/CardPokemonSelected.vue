<script setup>
import 'animate.css';
const pokemon = defineProps(['pokemon', 'loading'])

</script>

<template>
    <div 
    class="card p-5 cardPokemon"
    :class="{'animate__animated animate__fadeInLeft': !pokemon.loading}"
    >

        <div class="card-body">
            <img :src="pokemon.pokemon.sprites.other.dream_world.front_default" height="250" class="card-img-top pt-2" :alt="pokemon.pokemon?.name">
            <h5 class="card-title mt-3 text-center">{{ pokemon.pokemon?.name.toUpperCase() }}</h5>
            <hr/>
            <div class="col">
                <section>
                    <strong>XP: </strong>
                    <span>{{ pokemon.pokemon.base_experience }}</span>
                </section>
                <section>
                    <strong>Altura: </strong>
                    <span>{{ pokemon.pokemon.height }}</span>
                </section>
            </div>
           
        </div>
    </div>
</template>

<style>
.cardPokemon {
    height: 75vh;
  background: rgb(121, 63, 251);
  background: radial-gradient(circle, rgba(226, 108, 12, 0.8) 0%, rgba(187, 36, 36, 0.8) 100%);
  cursor: pointer;
}
</style>