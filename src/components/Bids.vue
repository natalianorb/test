<template>
  <table class="table">
      <tr class="table__head">
        <th class="table__th">Count</th>
        <th class="table__th">Total</th>
        <th class="table__th">Amount</th>
        <th class="table__th">Price</th>
      </tr>
      <tr class="table__tr" v-for="(item, index) in tableData" :key="index">
        <td class="table__td">{{ item.numberOfOrders }}</td>
        <td class="table__td" >{{ totals[index] }}</td>
        <td class="table__td">{{ item.quantity }}</td>
        <td class="table__td">{{ item.price }}</td>
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

<style lang="less">
@grey : #666;
.table {
  width: 100%;
  height: 95vh;
  overflow: hidden;
  border-collapse: collapse;
  border: 1px solid @grey;
  text-align: left;
  color: @grey;
  &__head {
    border-bottom: 1px solid @grey;
    .table__th:last-child {
      text-align: right;
    }
  }
  tbody {
    display: block;
    height: 200%;
    overflow-y: scroll;
  }
  &__th {
    padding: 10px;
    max-width: 112px;
    box-sizing: border-box;
    overflow: hidden;
    text-overflow: ellipsis;
    font-style: italic;
    color: #000;
  }
  &__tr {
    td:last-child {
      text-align: right;
    }
  }
  &__td {
    padding: 5px 10px;
  }
}

</style>
