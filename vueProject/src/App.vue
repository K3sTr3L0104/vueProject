<script setup>
import HelloWorld from './components/HelloWorld.vue'
import { ref } from 'vue';
import { recipes } from '../data/dummyData';
var receptek = ref([recipes]);
</script>

<template>

  <header>

  </header>
  <main>

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
</style>
