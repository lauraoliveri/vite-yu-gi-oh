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
    <main class="p-5">
        <div>
            <select class="form-select mb-4" aria-label="Default select example">
                <option selected>Alien</option>
                <option value="1">One</option>
                <option value="2">Two</option>
                <option value="3">Three</option>
            </select>


            <div class="white_background d-flex flex-wrap">
                <div v-for="(card, i) in store.Cards" :key="1" class="fs-5 fw-bold text-uppercase card_yugy">
                   
                    <div class="card_name">
                        {{ card.name }}
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
    height: 100vh;
    background-color: $MainColor;
}

.form-select {
    width: 100px;
}

div {
    width:100%;
    height:100%;

}

.white_background {
    width:100%;
    height:95%;
    background-color: white;
    margin: 0 auto;
    padding: 40px;
}

.card_yugy {
    width: calc(100% / 6);
    max-height: 300px;
    margin: 6px;
}

.card_name {
    border: 1px solid red;
    background-color: $MainColor;
}
</style>