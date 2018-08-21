<template>
  <div id="app">
    <OrderTable :data="data"/>
  </div>
</template>

<script>
import OrderTable from './components/OrderTable'
import data from './data1.json'

export default {
  name: 'App',
  components: {
    OrderTable
  },
  data: data
}
</script>

<style>
#app {
}
</style>
