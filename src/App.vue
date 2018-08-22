<template>
  <div id="app">
    <table class="table">
      <caption>Order Book</caption>
      <thead class="table__head">
        <tr>
          <th class="table__th _left">Count</th>
          <th class="table__th _left">Total</th>
          <th class="table__th _left">Amount</th>
          <th class="table__th _right">Price</th>

          <th class="table__th _left">Count</th>
          <th class="table__th _right">Total</th>
          <th class="table__th _right">Amount</th>
          <th class="table__th _right">Price</th>
        </tr>
      </thead>
      <Body :table-data="data"/>
    </table>
  </div>
</template>

<script>
import Body from './components/Body.vue'
import * as data1 from './data1.js'

export default {
  name: 'table',
  components: {
    Body
  },
  data () {
    return data1
  }
}
</script>

<style lang="less">
@grey : #666;
 .app {
  min-width: 900px;
  max-width: 1920px;
  font: 14px sans-serif;
}
._left {
  text-align: left;
}
._right {
  text-align: right;
}

.table {
  width: 100%;
  border-collapse: collapse;
  border: 1px solid @grey;
  font: 14px sans-serif;

  &__head {
    display: block;
    border-bottom: 1px solid @grey;
  }
  &__body {
    display: block;
    height: 600px;
    overflow: hidden;
    &:hover {
      overflow-y: scroll;
    }
    color: @grey;
  }
  &__th {
    min-width: 112px;
    padding: 10px;
    overflow: hidden;
    text-overflow: ellipsis;
    box-sizing: border-box;
    font-style: italic;
    color: #000;
  }
  &__td {
    min-width: 112px;
    max-width: 240px;
    padding: 5px 10px;
    box-sizing: border-box;
  }

  th:nth-child(2),
  td:nth-child(2),
  th:nth-child(3),
  td:nth-child(3),
  th:nth-child(6),
  td:nth-child(6),
  th:nth-child(7),
  td:nth-child(7)  {
    min-width: 160px;
  }

}
</style>
