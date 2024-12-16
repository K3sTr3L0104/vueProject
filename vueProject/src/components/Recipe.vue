<script setup>
import { ref, defineEmits } from 'vue';
import { recipes } from '../../data/dummyData';
const emit = defineEmits(['addNewRecipe']);
var difficulty = ref("")
var name = ref("")
var cookTime = ref(0)
var imageURL = "https://via.placeholder.com/300x200";
const join = () =>{
    var obj = {name: name.value,cookTime: cookTime.value,difficulty: difficulty.value, imageUrl: imageURL};
    recipes.push(obj)
    console.log(recipes)
    emit('addNewRecipe',obj)
    alert("Sikeres feltöltés!")
    name.value = "";
    difficulty.value = "";
    cookTime.value = 0;
}
</script>
<template>
    <header>
    </header>
    <main>
        <section>
            <div class=" newRecipe card text-center">
            <div class="card-header">
                Receptek
            </div>
            <div class="card-body">
                <h5 class="card-title">Új recept hozzáadása</h5>

                <div class="input-group mb-3">
                <input type="text" class="form-control" placeholder="Recept neve" aria-label="Recept neve" aria-describedby="button-addon2" v-model="name">
                </div>

                <div class="input-group mb-3">
                <input type="number" class="form-control" placeholder="elkészítési idő" aria-label="Elkészítési idő" aria-describedby="button-addon2" v-model="cookTime">
            
                </div>

                <div class="input-group mb-3">
                <label class="input-group-text" for="inputGroupSelect01">Nehézség</label>
                <select class="form-select" id="inputGroupSelect01" v-model="difficulty">
                    <option>könnyű</option>
                    <option>közepes</option>
                    <option>nehéz</option>
                </select>
                </div>
                
                <a href="#" class="btn btn-primary" @click="join()">Hozzáadás</a>
            </div>
            <div class="card-footer text-muted">
                Receptek
            </div>
            </div>
        </section>

    </main>
    <footer>

    </footer>

</template>
<style scoped>

.newRecipe{
    margin-top:20px;
}

</style>