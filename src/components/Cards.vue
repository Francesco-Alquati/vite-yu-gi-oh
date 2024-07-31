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
            <div class="col-3 my-3" v-for="card in store.cardsList" :key="card.id">
                <div class="bg-yugi min-wh b-grey d-flex flex-column align-items-center justify-content-center text-white text-center">
                    <img :src="card.card_images[0].image_url" />
                    <h6 class="mt-3">{{ card.name }}</h6>
                    <div class="mt-3">
                        <span v-if="card.archetype">{{ card.archetype }}</span>
                        <div v-else>unchnown</div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<style lang="scss" scoped>
    img{
        height: 200px;
        width: 150px;
    }
    .min-wh{
        min-height: 400px;
        min-width: 280px;
    }
    .b-grey{
        border: 2px solid rgb(86, 86, 86);
    }
    .bg-yugi{
        background-image: url('https://orig10.deviantart.net/69f2/f/2016/289/4/1/ygo_card_backing__final__by_icycatelf-dal6wsb.png');
        background-size: cover;
    }
</style>