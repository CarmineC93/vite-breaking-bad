<script>
import { store } from "../store";
export default {
    name: "AppFilter",
    data() {
        return {
            store,
            categoryOptions: ["Breaking Bad", "Better Call Saul"]
        }
    }
}
</script>

<template>
    <div class="filter d-flex justify-content-center">
        <select class="form-select" aria-label="Default select example">
            <option selected value="">Select Series</option>
            <!-- creo un'opzione per ogni elemento nell'array categoryOptions -->
            <option v-for="(option, index) in categoryOptions" :value="option" :key="index">{{ option }}</option>
        </select>
        <!-- collego all'azione click l'evento search che viene trasmetto al genitore tramite $emit -->
        <button class="btn btn-success mx-1" @click="$emit('search')">Filter</button>
    </div>
</template>

<style lang="scss" scoped>
.filter{
    width: 30%;
    margin: 1.5rem 0;
}
</style>