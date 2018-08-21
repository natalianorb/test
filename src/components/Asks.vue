<template>
  <table class="table">
      <tr class="table__head">
        <th class="table__th">Price</th>
        <th class="table__th">Amount</th>
        <th class="table__th">Total</th>
        <th class="table__th">Count</th>
      </tr>
      <tr class="table__tr" v-for="(item, index) in tableData" :key="index">
        <td class="table__td">{{ item.price }}</td>
        <td class="table__td">{{ item.quantity }}</td>
        <td class="table__td" >{{ totals[index] }}</td>
        <td class="table__td">{{ item.numberOfOrders }}</td>
      </tr>
  </table>
</template>

<script>
export default {
  props: ['tableData'],
  computed: {
    totals () {
      let res = []
      this.tableData.forEach((item, index, array) => {
        res.push(index ? item.quantity + res[index - 1] : item.quantity)
      })
      return res
    }
  }
}
</script>

<style scoped lang="less">
 table {
    border-left: none;
    text-align: right;
    .table__th:first-child {
      text-align: left;
    }
    .table__tr {
      td:first-child {
        text-align: left;
      }
    }
  }
</style>
