<script>
import { store } from '../store.js';
export default {
    data() {
        return {
            store,
        }
    },
}
</script>
<template>
    <div class="container">
        <div class="row">
            <div class="col-3" v-for="card in store.cardsList" :key="card.id">
                <img :src="card.image_url" alt="">
                <div class="text-white">
                    {{ card.name }}
                    {{ card.archetype }}
                </div>
            </div>
        </div>
    </div>
</template>
<style lang="scss">
    .b-white{
        border: 10px solid white;
    }
    img{
        height: 80%;
        width: 80%;
    }
</style>