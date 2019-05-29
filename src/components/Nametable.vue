<template>
  <div id="app">
    <SortedTable :values="values">
      <thead>
        <tr>
          <th scope="col" style="text-align: left; width: 10rem;">
            <SortLink name="name">Name</SortLink>
          </th>
          <th scope="col" style="text-align: left; width: 10rem;">
            <SortLink name="age">age</SortLink>
          </th>
          <th scope="col" style="text-align: left; width: 10rem;">
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
export default {
  name: 'Nametable',
  props: ['values']
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
