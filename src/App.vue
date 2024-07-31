<script>
import { store } from './store.js';
import  axios  from 'axios';
import AppHeader from './components/AppHeader.vue';
import Cards from './components/Cards.vue';

export default{
  components:{
    AppHeader,
    Cards,
    
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
  </div>
  <div class="container mt-2">
    <div class="row">
        <div class="col-12">
          
        </div>
    </div>
    <div class="row">
      <div class="">
        <Cards />
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
  background-image: url('https://www.yugioh-card.com/eu/wp-content/uploads/2022/09/WCQ-hero-banner.webp');
  background-size: contain;
  
}
select{
  width: 120px;
}

</style>
