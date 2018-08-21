<template>
  <div id="app">
    <div class="app">
      <div class="app__left">
        <Bids :table-data="data.bids"/>
      </div>
      <div class="app__right">
        <Asks :table-data="data.asks"/>
      </div>
    </div>
  </div>
</template>

<script>
import Bids from './components/Bids'
import Asks from './components/Asks'
import * as data1 from './data1.js'

export default {
  name: 'App',
  components: {
    Bids,
    Asks
  },
  data () {
    return data1
  }
}
</script>

<style lang="less">
.app {
  display: flex;
  min-width: 900px;
  max-width: 1920px;
  font: 14px sans-serif;
  &__left,
  &__right {
    width: 50%;
  }
}
</style>
