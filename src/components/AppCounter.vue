<script>
import { store } from "../store";

export default {
    name: "AppCounter",
    data() {
        return {
            store
        }
    },
    computed: {
        charactersNumber() {
            return this.store.characters.length;
        }
    }
}
</script>

<template>
    <div>
        <p v-if="charactersNumber === 0">Non ci sono risultati per la tua ricerca</p>
        <p v-else>
            Abbiamo trovato {{ charactersNumber }}
            {{ charactersNumber === 1 ? 'personaggio' : 'personaggi' }}
        </p>
    </div>
</template>

<style lang="scss" scoped>

    p{
        padding: 0.5rem 1rem;
        background-color: rgb(4, 100, 40);
        color: white;
        border-radius: 20px;
        text-align: center;
    }

</style>