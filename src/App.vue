<script>
import { store } from './store.js';
import { axios } from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
export default{
  component:{
    AppHeader,
    AppMain,
  },
  created() {
    
  },
  methods: {
    getCardsList(){
      axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0').then((result) =>{
        store.cardsList = result.data;
      });
    }
  },
  data() {
    return {
      store,
    }
  },
}

</script>

<template>
 <header>

 </header>
 <main>

 </main>
</template>

<style lang="scss">
@import './styles/generals.scss'
</style>
