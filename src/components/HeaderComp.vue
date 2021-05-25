<template>
  <header>
    <div class="box-logo col-1 ">
        <div class="logo">
          <img src="../assets/img/logo-small.svg" alt="">
        </div>
    </div>

    <div class="offset-9 col-1">
      <select name="album" id="generi" placeholder="Generi">
        <option
        @click="resetString()" 
        value="all">
          All
        </option>
        <option
        v-for="(gender, index) in genders" :key="index"
        @click="writeString(gender.genre)"
        value="gender.genre">
        {{gender.genre}}
        </option>
      </select>
    </div>
  </header>
</template>

<script>
export default {
 name:'HeaderComp',
 data(){
   return{
     strSearch:'',
   }
 },
 props:{
   genders:Array
 },
 methods:{
   writeString(object){
     this.$emit("searchGender",this.strSearch = object);
     console.log(this.strSearch);
   },
   resetString(){
     this.strSearch ="";
     this.writeString('');
   }
 }
}
</script>

<style lang="scss" scoped>
header{
  height: 80px;
  background-color:#2E3A46 ;
  display: flex;
  align-items: center;
  .box-logo{
    .logo{
      height: 60px;
      width: 60px;
      border-radius: 50%;
      background-color: #2E3A46;
      margin-left: 20px;
    };
  };
}
</style>