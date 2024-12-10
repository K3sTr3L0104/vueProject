<script setup>
import HelloWorld from './components/HelloWorld.vue'
import { ref } from 'vue';
import { recipes } from '../data/dummyData';
var receptek = ref([recipes]);
</script>

<template>

  <header>
    <section>

<nav class="navbar navbar-expand-lg bg-body-tertiary">
<div class="container-fluid">
  <a class="navbar-brand" href="#">Receptkönyv</a>
  <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>
  <div class="collapse navbar-collapse" id="navbarNav">
    <ul class="navbar-nav">
      <li class="nav-item">
        <a class="nav-link active" aria-current="page" href="#">Receptek</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">Új recept</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">Kedvencek</a>
      </li>
    </ul>
  </div>
</div>
</nav>

</section>

</header>

  <main>

  <section>
      <div class="d-flex align-items-center">
        <div class="searchBar form-outline flex-fill w-50" data-mdb-input-init>
          <input type="search" id="form1" class="form-control" placeholder="Keress receptet..." aria-label="Search" />
        </div>
        <select class=" select1 form-select w-25" aria-label="Default select example">
          <option selected>Minden nehézség</option>
          <option value="1">One</option>
          <option value="2">Two</option>
          <option value="3">Three</option>
        </select>
        <select class="select2 form-select w-25" aria-label="Default select example">
          <option selected>Elkészítési idő szerint</option>
          <option value="1">One</option>
          <option value="2">Two</option>
          <option value="3">Three</option>
        </select>
      </div>
    </section>

    <section>

      <div class="row row-cols-1 row-cols-md-3 g-4">
      <div class="col" v-for="recipe in recipes">
        <div class="card h-100">
          <img :src="recipe.imageUrl" class="card-img-top" alt="...">        
          <div class="card-body">
            <h5 class="card-title">{{recipe.name}}</h5>
            <p class="card-text">Elkészítési idő: {{ recipe.cookTime }} perc</p>
            <div>
            <span class="badge" :class="{ 'bg-success': recipe.difficulty === 'könnyű', 'bg-warning': recipe.difficulty === 'közepes', 'bg-danger': recipe.difficulty === 'nehéz' }">{{ recipe.difficulty }}</span>
          </div>
            <button class="btn btn-primary" type="submit">Button</button>
          </div>
        </div>
      </div>
    </div>

    </section>

    <HelloWorld/>
  </main>
  <footer>

  </footer>
  
  
</template>

<style scoped>
span{
  margin-bottom: 25px;
}

.searchBar{
  margin-top: 25px;
  margin-bottom: 25px;
}

.select1{
  margin-left: 20px;
  margin-right: 20px;
}
</style>
