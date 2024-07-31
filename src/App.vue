<script>
import { store } from './store.js';
import  axios  from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
export default{
  components:{
    AppHeader,
    AppMain,
  },
  created() {
    this.getCardsList();
  },
  methods: {
    getCardsList(){
      axios.get(store.apiUrl).then((result) =>{
        store.cardsList = result.data.data;
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
  <AppHeader />
 </header>
 <main>
  <div class="container">
    <div class="row">

    </div>
  </div>

 </main>
</template>

<style lang="scss">
@import './styles/generals.scss';
</style>
