<script>
import { store } from './store.js';
import  axios  from 'axios';
import AppHeader from './components/AppHeader.vue';
import Cards from './components/Cards.vue';
import AppLoader from './components/AppLoader.vue';
import AppSearchArchetype from './components/AppSearchArchetype.vue';

export default{
  components:{
    AppHeader,
    Cards,
    AppLoader,
    AppSearchArchetype,
    
  },
  created() {
    this.getCards();
    this.getArchetype();
  },
  methods: {
    getCards(){
      if(store.archetype_search !== ''){
          axios.get(`${store.apiUrl}&archetype=${store.archetype_search}`).then((response) =>{
          store.cardsList = response.data.data;
          store.loading = false;
        });
      }
      else{
          axios.get(store.apiUrl).then((response) =>{
          store.cardsList = response.data.data;
          store.loading = false;
        });
      }
    },
    getArchetype(){
      axios.get(store.apiArchetypeUrl).then((response) => {
        for(let i = 0; i<30; i++){
          store.archetypeList.push(response.data[i]) ;
        }
        
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
    <div class="row" >
      <div class="col-12 text-center mb-3">
      <AppSearchArchetype @filter_cards="getCards()"/>
      </div>
      <AppLoader  v-if="store.loading"/>
      <div class="col-12" v-else>
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
