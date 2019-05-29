<template>
  <div class="hello">

   <div class="container">
     <div class="rest-images" v-for="image in photoes">
      
     </div>
   </div>
  </div>
</template>

<script>
export default {
  name: 'Paginate',
  props: ['options']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
   justify-content: center;
}
</style>
