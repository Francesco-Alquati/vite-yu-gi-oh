<script>
import { store } from './store.js';
import  axios  from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppCards from './components/AppCards.vue';

export default{
  components:{
    AppHeader,
    AppCards,
    
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
      <div class="col-12">
        <select class="mt-5" v-model="selectedArchetype" name="archetype" id="">
          <option value="option1">Alien</option>
        </select>
      </div>
    </div>
    <div class="row">
      <div class="col-12">
        <AppCards />
      </div>
    </div>
  </div>

 </main>
</template>

<style lang="scss">
@import './styles/generals.scss';
main{
  min-height: calc(100vh - 88px); 
  margin: 0; 
  padding: 0; 
  background-image: url('https://www.yugioh-card.com/eu/wp-content/uploads/2022/09/OTS-hero-banner-v02.webp');
  background-size: cover;
}
select{
  width: 120px;
}

</style>
