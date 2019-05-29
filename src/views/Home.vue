<template>
  <div id="inner-content">
  	<p>(Use any public API or make own to load JSON with 5000+ records)
    <br>
        <span style="font-size:12px">Data souce I used:https://jsonplaceholder.typicode.com</span>
    </p>
   <Photo v-bind:photoes="photoes" />
  </div>
</template>

<script>
import Photo from '../components/Photo.vue'
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    Photo
  },
    data(){
        return{
            photoes:[]
       }

    },
    created(){
        axios.get('https://jsonplaceholder.typicode.com/photos?_limit=500')
        .then(res => this.photoes = res.data);
    }
}
</script>

<style >
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
