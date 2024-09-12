<script>
import AppCards from './AppCards.vue';
import { store } from '../store';

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


            <div class="white_background">
                <div v-for="(card, i) in store.Cards" :key="1">
                   
                    {{ card.name }}
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
    width:95%;
    height:95%;
    background-color: white;
    margin: 0 auto;
}
</style>