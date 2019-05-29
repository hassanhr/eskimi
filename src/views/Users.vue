<template>
  <div id="inner-content">
    <p>A) Use vanilla JS or any framework you like to implement data representation table (at least 3 columns) <br> B) Click on any column header it should sort the table by particular column, next click should reverse order <br>
      <span style="color:red">Please click any column header of the table</span><br>
        <span style="font-size:12px">Data souce I used:https://api.myjson.com/bins/s9lux</span>
    </p>

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
  name: 'Users',
  components: {
    Nametable
  },
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

</style>
