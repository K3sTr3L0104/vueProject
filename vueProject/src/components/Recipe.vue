<script setup>

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
                <input type="text" class="form-control" placeholder="Recept neve" aria-label="Recept neve" aria-describedby="button-addon2">
                </div>

                <div class="input-group mb-3">
                <input type="number" class="form-control" placeholder="elkészítési idő" aria-label="Elkészítési idő" aria-describedby="button-addon2">
            
                </div>

                <div class="input-group mb-3">
                <label class="input-group-text" for="inputGroupSelect01">Nehézség</label>
                <select class="form-select" id="inputGroupSelect01">
                    <option value="1">Könnyű</option>
                    <option value="2">Közepes</option>
                    <option value="3">Nehéz</option>
                </select>
                </div>
                
                <a href="#" class="btn btn-primary">Hozzáadás</a>
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