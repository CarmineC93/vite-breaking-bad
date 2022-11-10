<script>
import { store } from "../store";
import AppCard from "./AppCard.vue";

export default {
    name: "AppGrid",
    components:{
        AppCard
    },
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <div class="grid">
        <div class="row m-2 g-3">
            <div class="col-5 col-md-3 col-sm-5" v-for="character in store.characters" :key="character.char_id">
                <AppCard :character="character" />
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>

.grid{
    background-color: white;
}

</style>