<template>
  <main class="d-flex">
    <section class="box-discs col-10 offset-1">
      <div 
      v-for="(disc, index) in discs" :key="index"
      class="box-disc col-12 col-md-6 col-lg-2 p-3 m-0 p-lg-0 m-lg-3 text-center">

        <div class="box-background p-3">
          <img class="img-fluid" :src="disc.poster" :alt="disc.title">
          <h3>{{disc.title}}</h3>
          <h4>{{disc.author}}</h4>
          <h4>{{disc.year}}</h4>
        </div>

      </div>
    </section>

  </main>
</template>

<script>
export default {
 name:'MainComp',
 props:{
   discs: Array
 }
};
</script>

<style lang="scss" scoped>
main{
  background-color:#1E2D3B ;
  padding: 100px 0;
  .box-discs{
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    
    .box-disc{
      .box-background{
        background-color:#2E3A46 ;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-items: center;
        height: 100%;
        &:hover{
          transform: scale(1.05, 1.05);
          filter:brightness(110%);
          box-shadow: 0 15px 15px rgba(0,0,0,.3);
        }
        img{
          width: 100%;
        };
        h3{
          color: #FFFFFF;
          font-size: 20px;
          text-transform: uppercase;
          font-weight: bold;
          margin:30px 0;
          margin-top: 8px;
        };
        h4{
          font-size: 15px;
          color:#737771; 
          margin-bottom: 0;  
  
        };
      };
    };
  };
};
</style>