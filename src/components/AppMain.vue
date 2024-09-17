<script>
import AppCards from './AppCards.vue';
import { store } from '../store';
export default {
  data() {
    return { 
     store:store
    }
  }
}


</script>


<template>
    <main class="p-5 container-fluid">
        <div class="row">
            <div  class="col">
                <!-- Select per il tipo di archetipo della card  -->
                <select class="form-select mb-4" aria-label="Default select example">
                    <option value="1" v-for="(archetype, i) in store.Archetypes" :key="1">{{ Archetypes.archetype }}</option>
                    
                </select>
    
                <!-- Numero di carte trovate -->
                <p class="fw-bold text-uppercase d-flex justify-content-center align-items-center ">
                    Found {{ store.Cards.length }} cards
                </p>

                <!-- Sfondo bianco -->
                <div class="white_background d-flex flex-wrap justify-content-center align-items-center p-0">

                    <!-- Ciclo per creare le card con propria immagine, nome e archetipo -->
                    <div v-for="(card, i) in store.Cards" :key="1" class="card_yugy">
                        <div>
                            <img :src="card.card_images[0].image_url" alt="card.name">
                        </div>
                        <div class="card_name fw-bold text-uppercase ">
                            {{ card.name }}
                           <div class="text-smaller text-black">
                            {{ card.archetype }}
                           </div>
                        </div>
                
                    </div>
                </div>
            </div>
        </div>
    </main>

</template>


<style lang="scss" scoped>

@use '../assets/scss/partials/variables' as *;

main {
    width: 100vw;
    background-color: $MainColor;
}

.form-select {
    width: 100px;
}



.white_background {
    width:100%;
    background-color: white;
    margin: 0 auto;
}

.card_yugy {
    width: calc(100% / 6);
    margin: 6px;
    padding: 20px;
}

.card_name {
    background-color: $MainColor;
    height: 80px;
    text-align: center;
    padding: 5px;
    color: white;
}

p {
    background-color: #212529;
    color: white;
}

img {
    width: 100%;
}
</style>