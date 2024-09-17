<script>
/* 
  Per importare ed utilizzare un componente dentro un altro devo SEMPRE seguire questi 3 passi:
  1) Importazione del componente
  2) Dichiarazione del componente
  3) Utilizzo del componente
*/
// 1) Importazione del componente
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppCards from './components/AppCards.vue';
import axios from 'axios';
import { store } from './store.js';

export default {
  data() {
    return { 
    store:store,
    }
  },
  // 2) Dichiarazione del componente
  components: {
    AppHeader,
    AppMain,
    AppCards
  },
  created() {
    // per prendere dall'API generale le info di ogni card
    axios 
    .get ('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=10&offset=0')
    .then((response)=> {

      console.log(response.data.data)
      this.store.Cards= response.data.data
      console.log(this.store.Cards)

      
    }),

    // per prendere dall'API degli archetipi tutti i tipi di archetipi che le card possono avere

    axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php')
    .then(response => {
      let archetypes = []
    // Ciclo for per aggiungere i nomi degli archetipi nell'array
    for (let i = 0; i < response.data.length; i++) {
        archetypes.push(response.data[i].archetype_name);
        
    }
    this.store.Archetypes = archetypes;
  })
  },
  methods: {
    
  }
}
</script>

<template>
  <div>
    <!-- 3) Utilizzo del componente -->
    <AppHeader />
    <AppMain />
    <AppCards />
    <main>
      
    </main>
  </div>
</template>

<style lang="scss">
@use 'assets/scss/main' as *;
// Import all of Bootstrap's CSS
@import "bootstrap/scss/bootstrap";
</style>
