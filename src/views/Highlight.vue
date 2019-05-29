<template>
  <div id="inner-content">
    <p> <span style="color:red">Attention please:</span> I was asked to do Output last clicked table cell data somewhere on the screen outside table. Change color of last clicked row. <br> <strong> why should I Change color of last clicked row, when I have to show last clicked cell data!</strong> <br> But I also did that it look like bugs (confiusing for user)! please click <a style="color:red" href="/#/highlight2">here</a><br><br>
      <span style="color:red">Please click any cell of the table</span><br>
        <span style="font-size:12px">Data souce I used:https://api.myjson.com/bins/s9lux</span>
    </p>
<div id="demoEl">
</div>
    <SortedTable :values="values">
      <thead>
        <tr>
          <th scope="col">
            <SortLink name="name">Name</SortLink>
          </th>
          <th scope="col">
            <SortLink name="age">age</SortLink>
          </th>
          <th scope="col">
            <SortLink name="gender">Gender</SortLink>
          </th>
        </tr>
      </thead>
      <tbody slot="body" slot-scope="sort">
        <tr v-for="value in sort.values" :key="value.id">
          <td>{{ value.name }}</td>
          <td>{{ value.age }}</td>
          <td>{{ value.gender }}</td>
        </tr>
      </tbody>
    </SortedTable>
  </div>
</template>

<script>

import Vue from 'vue';

import SortedTablePlugin from "vue-sorted-table";
Vue.use(SortedTablePlugin);

export default {
  name: 'Highlight',
 
   data: function() {
    return {
      values: []
    };
  },
    created:function() {
    fetch('https://api.myjson.com/bins/s9lux')
    .then(res => res.json())
    .then(res => {
      this.values = res;
    })
  },
   mounted() {

    setTimeout(function(){ 
    var all = document.getElementsByTagName("TD");
    for (var i=0, max=all.length; i < max; i++) {
     
      document.getElementsByTagName("td")[i].onclick = function(){
          document.getElementById("demoEl").innerHTML = this.innerHTML;
          var lights = document.getElementsByClassName("tdcolor");
          while (lights.length)
          lights[0].classList.remove("tdcolor");
          this.classList.add("tdcolor");
    
        }
    }
    
  
    }, 2000);
       
   }
}
</script>

<style scoped>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
#demoEl{
  font-size: 28px;
  color: green;
  height: 36px;
  margin-bottom: 20px;
}
table {
    min-width: 300px;
    width: 70%;
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
td.tdcolor {
  background-color: yellow;

}
</style>
