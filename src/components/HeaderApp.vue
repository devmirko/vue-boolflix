<template>
  <div class="container">
    <img src="../assets/Netflix-PNG.png" alt="">

   
  </div>
</template>

<script>
export default {
  name: 'HeaderApp',
 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.container{
   height: 70px;
   background-color: black;
   display: flex;
   align-items: center;

    img{
      width: 50px;
      height: 50px;
      margin-left: 10px;
    }
}

</style>
