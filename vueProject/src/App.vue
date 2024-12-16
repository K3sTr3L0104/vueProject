<script setup>
import { ref } from 'vue';
import HelloWorld from './components/HelloWorld.vue'
import Recipe from './components/Recipe.vue'
var newObj = ""
var asd = ref(0);
const newPage = () => {
  asd.value = 1;
  console.log(asd.value)
}

const kiegeszit = (obj)=>{
  console.log(newObj);
  asd.value = 0;
}

const oldPage = () => {
  asd.value = 0;
}
</script>

<template>

  <header>
    <section>

      <nav class="navbar navbar-expand-lg bg-body-tertiary">
        <div class="container-fluid">
          <a class="navbar-brand" href="#">Receptkönyv</a>
          <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
            aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav">
              <li class="nav-item">
                <a class="nav-link active" aria-current="page" href="#" @click="oldPage()">Receptek</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="#" @click="newPage()">Új recept</a>
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
    <HelloWorld v-if="asd == 0" :obj="newObj"/>
    <Recipe v-if="asd > 0" @addNewRecipe="kiegeszit"/> 
    
  </main>
  <footer>

  </footer>


</template>

<style scoped>
span {
  margin-bottom: 25px;
}

.searchBar {
  margin-top: 25px;
  margin-bottom: 25px;
}

.select1 {
  margin-left: 20px;
  margin-right: 20px;
}
</style>

