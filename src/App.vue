<script>
import axios from "axios";

import AppHeader from './components/AppHeader.vue';
import AppGrid from './components/AppGrid.vue';
import AppLoader from './components/AppLoader.vue';



import { store } from "./store";



export default {
  components: {
      AppHeader,
      AppGrid,
      AppLoader

  },
  data() {
    return {
      store
    }
  },
  created() {

    this.store.loading = true;
    axios.get("https://www.breakingbadapi.com/api/characters").then((resp) => {
      this.store.characters = resp.data;
      //loggo il proxy
      console.log(resp);
      //loggo l'array con i 62 oggetti/characters
      console.log(this.store.characters);
      //resetto loading a false perché i dati sono arrivati
      this.store.loading = false;
    });
  }
}

</script>

<template>
  <div class="wrapper">
    <AppHeader/>
    <main>
      <div class="container">
        <AppLoader v-if="store.loading" />
        <AppGrid v-else />
      </div>
    </main>
  </div>
</template>

<style lang="scss">
@use "./style/general.scss" as *;

</style>
