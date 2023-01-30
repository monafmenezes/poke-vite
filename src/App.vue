<script setup>
import { ref } from 'vue';

let num = ref(0)
</script>

<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
  <div class="container-fluid">
    <router-link class="navbar-brand" to="/">
      <img src="./assets/pikechu.svg" alt="Logo" width="30" height="24" class="d-inline-block align-text-top">
      Pokevite
    </router-link>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavDropdown" aria-controls="navbarNavDropdown" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNavDropdown">
      <ul class="navbar-nav">
        <li class="nav-item">
          <router-link class="nav-link" aria-current="page" to="/">Home</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" to="/about">About</router-link>
        </li>
      </ul>
    </div>
  </div>
</nav>

<div class="main">
  <router-view>

  </router-view>
</div>

<footer class="bg-primary text-light">
  <div>Design in {{ new Date().getFullYear() }}</div>
</footer>

</template>

<style>
body {
  height: 100vh;
  background: rgb(18,5,245);
  background: linear-gradient(90deg, rgba(18,5,245,0.6699054621848739) 0%, rgba(0,212,255,0.7203256302521008) 100%);
}
 footer {
  position: fixed;
  bottom: 0;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 56px;
 }
</style>
