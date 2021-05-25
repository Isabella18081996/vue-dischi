<template>
  <div id="app">

    <div v-if="!loading" >
      <HeaderComp
      :genders="arrGenders"
      @searchGender = 'searchingGender' />
      <MainComp :discs="arrDischiGenders" />
    </div>  

    <Loader title="Libreria dischi spotify" v-else />

  </div>
</template>

<script>
import axios from 'axios';
import HeaderComp from './components/HeaderComp.vue';
import MainComp from './components/MainComp.vue';
import Loader from '@/components/Loader.vue';


export default {
  name: 'App',
  data(){
    return{
      axios,
      arrDischi: [],
      loading:true,
      arrGenders:[],
      stringGender:'',
      arrDischiGenders:[],
    }
  },
created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(res =>{
      this.arrDischi = res.data.response;
      this.arrDischiGenders = this.arrDischi;
      this.arrGenders = res.data.response.filter( item =>{
        if(!this.arrGenders.includes(item.genre)){
          return this.arrGenders.push(item.genre)
        }
        console.log(this.arrGenders);
      });
      this.loading = false;
    })
    .catch(err =>{
      console.log(err);
    })
  },
  computed:{
    
  },
  methods:{
    
    searchingGender(text){
      this.stringGender = text;
      this.arrDischiGenders = this.arrDischi.filter( item =>{
        if(this.stringGender === item.genre){
          return true
        }else if(this.stringGender === ''){
          return this.arrDischiGenders = this.arrDischi
        }
      });
      console.log(this.arrDischiGenders);
      console.log(this.stringGender);
    }
   
  },
  components: {

    HeaderComp,
    MainComp,
    Loader
    
  }
}
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap';
@import '@/assets/style/general.scss';
</style>
