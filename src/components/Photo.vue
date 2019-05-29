<template>
  <div class="hello">

   <div class="container">
     <div class="rest-images" v-for="image in photoes">
       <img v-bind:src="image.thumbnailUrl" /> 
     </div>
   </div>
  </div>
</template>

<script>
export default {
  name: 'Photo',
  props: ['photoes']
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
