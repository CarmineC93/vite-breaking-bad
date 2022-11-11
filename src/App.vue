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
    //prima che l'utente possa filtrare i personaggi la pagina carica comunque tutti i personaggi
    //solo se le condizioni in methods sono true la chiamata viene modificata
    this.getCharacters() 
  },
  methods: {
    getCharacters() {
    // Prima che inizi la chiamata, metto loading a true
    this.store.loading = true;
    
    //salvo in una variabile l'API
    let apiUrl = "https://www.breakingbadapi.com/api/characters"; // ?category=Better+Call+Saul

    //creo oggetto di parametriAPI che andrò ad aggiungere se l'utente avrà dato un valore alla proprietà flag in store.js 
    let urlParams = {}
    console.log(this.store.searchCategory)
      if (this.store.searchCategory) {
        console.log(urlParams.category);
        urlParams.category = this.store.searchCategory;
      }
      console.log(urlParams)
      //con get facciamo chiamata dell'API + oggetto di parametriAPI il cui valore verrà assegnato sopra se l'utente ha dato un valore in store
      axios.get(apiUrl, {
        params: urlParams
      }).then((resp) => {
          //qui abbiamo la risposta e diciamo cosa farne
          this.store.characters = resp.data
          console.log(resp.data)
        })
        .catch(err => {
          //qui gestiamo eventuali errori(come l'assenza di valori validi)
          //in questo caso se nessun valore corrisponde alla ricerca, anzichè apparire un errore 404, svuotiamo semplicemente l'array
          this.store.characters = [];
        })
        .finally(() => {
          //infine resetto valore di proprietà flag loading, perchè ormai i valori sono arrivati
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
