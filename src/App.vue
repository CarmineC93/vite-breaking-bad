<script>
import axios from "axios";

import AppHeader from './components/AppHeader.vue';
import AppGrid from './components/AppGrid.vue';
import AppLoader from './components/AppLoader.vue';
import AppCounter from './components/AppCounter.vue';
import AppFilter from './components/AppFilter.vue';


import { store } from "./store";



export default {
  components: {
      AppHeader,
      AppGrid,
      AppLoader,
      AppCounter,
      AppFilter

  },
  data() {
    return {
      store
    }
  },
  created() {
    //prima che l'utente possa filtrare i personaggi l pagina carica comunque tutti i personaggi
    //solo se le condizioni in methods sono true la chiamata viene modificata
    this.getCharacters() 
  },
  methods: {
    getCharacters() {
    // Prima di iniziare la chiamata, metto loading a true
    this.store.loading = true;
    
    let apiUrl = "https://www.breakingbadapi.com/api/characters";
      // ?category=Better+Call+Saul
    //creo oggetto dei parametri dell'API che andrò ad aggiungere se l'utente avrà dato un valore alla proprietà flag in store 
    let urlParams = {}
      if (this.store.searchStatus) {
        urlParams.status = this.store.searchCategory;
        console.log(resp.data)

      }

      //con get facciamo chiamata dell'API + oggetto di parametriAPI il cui valore verrà assegnato sopra se l'utente ha dato un valore in store
      axios.get(apiUrl, {
        params: urlParams
      })
        //qui abbiamo la risposta e diciamo cosa farne
        .then((resp) => {
          this.store.characters = resp.data
        })
        //qui gestiamo eventuali errori(come l'assenza di valori validi)
        .catch(err => {
          this.store.characters = [];
        })
        //infine resetto valore di proprietà flag loading, perchè ormai i valori sono arrivati
        .finally(() => {
          this.store.loading = false;
        })

    }
  }
}

</script>

<template>
  <div class="wrapper">
    <AppHeader/>
    <AppFilter @search="getCharacters" />
/>
    <main>
      <div class="container">
        <AppCounter />
        <AppLoader v-if="store.loading" />
        <AppGrid v-else />
      </div>
    </main>
  </div>
</template>

<style lang="scss">
@use "./style/general.scss" as *;

</style>
