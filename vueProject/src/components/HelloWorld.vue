<script setup>
import { recipes } from '../../data/dummyData';
import { ref, watch } from 'vue';

var chose = ref("Elkészítési idő szerint");
var difficultyFilter = ref("Minden nehézség");
var selectedItems = ref([...recipes]);
var searchValue = ref("");

watch([chose, difficultyFilter, searchValue], () => {
  let filteredRecipes = [...recipes];
  if (searchValue.value) {
    filteredRecipes = filteredRecipes.filter(recipe => 
      recipe.name.toLowerCase().includes(searchValue.value.toLowerCase())
    );
  }

  if (difficultyFilter.value !== "Minden nehézség") {
    filteredRecipes = filteredRecipes.filter(recipe => recipe.difficulty === difficultyFilter.value);
  }

  if (chose.value === "növekvő") {
    filteredRecipes.sort((a, b) => a.cookTime - b.cookTime);
  } else if (chose.value === "sort") {
    filteredRecipes.sort((a, b) => a.name.localeCompare(b.name));
  }

  selectedItems.value = filteredRecipes;
  console.log(selectedItems.value);
});
</script>


<template>
    <main>
  
      <section>
        <div class="d-flex align-items-center">
          <div class="searchBar form-outline flex-fill w-50" data-mdb-input-init>
            <input type="search" id="form1" class="form-control" placeholder="Keress receptet..." aria-label="Search" v-model="searchValue" />
          </div>

          <select class="select1 form-select w-25" aria-label="Default select example" v-model="difficultyFilter">
            <option value="Minden nehézség">Minden nehézség</option>
            <option value="könnyű">Könnyű</option>
            <option value="közepes">Közepes</option>
            <option value="nehéz">Nehéz</option>
          </select>

          <select class="select2 form-select w-25" aria-label="Default select example" v-model="chose">
            <option value="Elkészítési idő szerint">Elkészítési idő szerint</option>
            <option value="növekvő">Növekvő</option>
            <option value="sort">ABC Sorrend</option>
          </select>
        </div>
      </section>
  
      <section>
  
        <div class="row row-cols-1 row-cols-md-3 g-4">
          <div class="col" v-for="recipe in selectedItems" :key="recipe.name">
            <div class="card h-100">
              <img :src="recipe.imageUrl" class="card-img-top" alt="...">
              <div class="card-body">
                <h5 class="card-title">{{ recipe.name }}</h5>
                <p class="card-text">Elkészítési idő: {{ recipe.cookTime }} perc</p>
                <div>
                  <span class="badge"
                    :class="{ 'bg-success': recipe.difficulty === 'könnyű', 'bg-warning': recipe.difficulty === 'közepes', 'bg-danger': recipe.difficulty === 'nehéz' }">
                    {{ recipe.difficulty }}
                  </span>
                </div>
                <button class="btn btn-primary" type="submit">Részletek</button>
              </div>
            </div>
          </div>
        </div>
  
      </section>
    </main>
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
