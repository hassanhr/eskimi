<template>
  <div id="inner-content">
  	<p>(Pagination with show all facility)
  <div class="pagecontent">
    <div v-if="display" >
         <paginate name="items" :list="items" :per="10" class="paginate-list">
          <table>
            <thead>
                <tr>
                    <th style="text-align: center;">ID</th>
                    <th>Email</th>
                </tr>
            </thead>
        
          <tbody>
              <tr v-for="item in paginated('items')">
                  <td style="text-align: center;"> {{ item.id }}</td>
                  <td> {{ item.email }}</td>
              </tr>
          </tbody>
           </table>
          </paginate>
           <paginate-links for="items" :show-step-links="true"></paginate-links>
            <button @click="display = !display">Show all</button>
      </div>
      <div v-else>
           <paginate name="items" :list="items" :per="100" class="paginate-list">
          <table>
            <thead>
                <tr>
                    <th style="text-align: center;">ID</th>
                    <th>Email</th>
                </tr>
            </thead>
        
          <tbody>
              <tr v-for="item in paginated('items')">
                  <td style="text-align: center;"> {{ item.id }}</td>
                  <td> {{ item.email }}</td>
              </tr>
          </tbody>
           </table>
          </paginate>
          <paginate-links for="items" :show-step-links="true"></paginate-links>
      </div>
  </div>
 

  </div>
</template>

<script>
 import Vue from 'vue';
 window.Vue = Vue;
import VuePaginate from 'vue-paginate'
Vue.use(VuePaginate)
import axios from 'axios'

export default {
  name: 'Datapage',
  
    data(){
        return{
            items: [],
            paginate: ['items'],
            display: true
       }

    },
      created:function() {
    fetch('https://jsonplaceholder.typicode.com/comments?_limit=100')
    .then(res => res.json())
    .then(res => {
      this.items = res;
    })
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}
.paginate-list {
  width: 159px;
  margin: 0 auto;
  text-align: left;
 
}
 .paginate-list li {
    display: block;
  
  }
 .paginate-list li:before {
      content: '';
      font-weight: bold;
      color: slategray;
    }
.paginate-list {
    width: 70%!important;
}
table {
    width: 100%;
    background-color: #f2f2f2;
    border-collapse: collapse;
    margin: auto;
}
th {
    padding: 5px;
}
th a {
    color: #000;
    text-decoration: none;
}
tr {
    border: 1px solid #000;
}
td {
    padding: 5px;
}
.number.active {
  color: red;
}
.left-arrow a,
.right-arrow a{
  color: green!important;
}
.paginate-links.items a{
    cursor: pointer;
}
.disabled a{
    cursor: not-allowed!important;
}
.pagecontent {
    margin-bottom: 50px;
}
</style>
