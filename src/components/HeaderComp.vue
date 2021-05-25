<template>
  <header>
    <div class="box-logo col-1 ">
        <div class="logo">
          <img src="../assets/img/logo-small.svg" alt="">
        </div>
    </div>
  </header>
</template>

<script>
export default {
 name:'HeaderComp'
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