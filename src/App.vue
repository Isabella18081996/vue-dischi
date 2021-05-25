<template>
  <div id="app">

    <div v-if="!loading" >
      <HeaderComp />
      <MainComp :discs="arrDischi" />
    </div>  

    <Loader title="Libreria dischi spotify" v-else />

  </div>
</template>

<script>
import axios from 'axios';
import HeaderComp from './components/HeaderComp.vue';
import MainComp from './components/MainComp.vue';
import Loader from '@/components/Loader.vue'


export default {
  name: 'App',
  data(){
    return{
      axios,
      arrDischi: [],
      loading:true,
    }
  },
  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(res =>{
      console.log(res.data.response);
      this.arrDischi = res.data.response;
      this.loading = false;
      
    })
    .catch(err =>{
      console.log(err);
    })
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
