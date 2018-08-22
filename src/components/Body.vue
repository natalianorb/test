<template>
  <tbody class="table__body">
    <tr v-for="(row,  i) of rows" :key="i">
      <template v-if="tableData.bids[i]">
        <td class="table__td _left">{{ tableData.bids[i].numberOfOrders }}</td>
        <td class="table__td _left">{{ bidsTotals[i] }}</td>
        <td class="table__td _left">{{ tableData.bids[i].quantity }}</td>
        <td class="table__td _right">{{ tableData.bids[i].price }}</td>
      </template>

      <template v-if="tableData.asks[i]">
        <td class="table__td _left">{{ tableData.asks[i].price }}</td>
        <td class="table__td _right">{{ tableData.asks[i].quantity }}</td>
        <td class="table__td _right">{{ asksTotals[i] }}</td>
        <td class="table__td _right">{{ tableData.asks[i].numberOfOrders }}</td>
      </template>
    </tr>
  </tbody>
</template>

<script>
export default {
  props: ['tableData'],
  computed: {
    rows () {
      return this.tableData.bids.length > this.tableData.asks.length ? this.tableData.bids : this.tableData.asks
    },
    bidsTotals () {
      let res = []
      this.tableData.bids.forEach((item, index, array) => {
        res.push(index ? item.quantity + res[index - 1] : item.quantity)
      })
      return res
    },
    asksTotals () {
      let res = []
      this.tableData.bids.forEach((item, index, array) => {
        res.push(index ? item.quantity + res[index - 1] : item.quantity)
      })
      return res
    }
  }
}
</script>

<style lang="less">

</style>
