<template>
  <TableInventories msg="Inventories"/>
</template>

<script>
import TableInventories from './components/TableInventories.vue'


export default {
  name: 'App',
  components: {
    TableInventories,
  }
  
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
