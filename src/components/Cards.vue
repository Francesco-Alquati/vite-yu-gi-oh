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
    <div class="container-fluid">
        <div class="row">
            <div class="col-3 my-3" v-for="card in store.cardsList" :key="card.id">
                <div class="bg-yugi min-wh b-grey position-relative d-flex flex-column align-items-center justify-content-center text-white text-center">
                    <div class="text-uppercase p-absolute-t fs-14">Konami</div>
                    <img :src="card.card_images[0].image_url" />
                    <h6 class="mt-3">{{ card.name }}</h6>
                    <div class="mt-3">
                        <span v-if="card.archetype">{{ card.archetype }}</span>
                        <div v-else>unchnown</div>
                    </div>
                    <div class="p-absolute-b">
                        <img src="/yugi-png.png" alt="">
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
    .p-absolute-t{
        position: absolute;
        top: 14px;
        left: 20px;
    }
    .p-absolute-b{
        position: absolute;
        bottom: -10px;
        right: 13px;
    }
    .p-absolute-b img{
        width: 70px;
        height: 70px;
    }
    .min-wh{
        min-height: 450px;
        min-width: 310px;
    }
    .b-grey{
        border: 2px solid rgb(86, 86, 86);
    }
    .bg-yugi{
        background-image: url('https://orig10.deviantart.net/69f2/f/2016/289/4/1/ygo_card_backing__final__by_icycatelf-dal6wsb.png');
        background-size: cover;
    }
    .fs-14{
        font-size: 14px;
    }
</style>