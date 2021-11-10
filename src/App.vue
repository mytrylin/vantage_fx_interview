<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <div >
    {{dataTest}}
    <button @click="fetchAPI">TESTBTN</button>
    <p>{{fetchTest}}</p>
    <vantage :msg="fetchTest + 1" :inemit="getEmitData"  @emitevent="emitAdd"></vantage>
    <p>{{getEmitData}}</p>
  </div>
</template>

<script>
import Vantage from './components/Vantage.vue'

export default {
  name: 'App',
  components: {
    Vantage
  },
  data() {
    return {
      dataTest: 'dataTest',
      fetchTest: {},
      getEmitData: 0
    }
  },
  computed: {
  },
  methods: {
    emitAdd(val) {
      this.getEmitData = val + val
    },
    fetchAPI() {
      fetch('https://api.coingecko.com/api/v3/exchange_rates')
        .then((res) => {
          console.log('api res')
          console.log(res)

          this.fetchTest = res.status
          console.log('this.fetchTest:')
          console.log(this.fetchTest)
        })
    },
    fetchAPI2() {
      fetch('https://api.coingecko.com/api/v3/exchange_rates')
        .then((res) => {
          this.fetchTest = res.status - 1
        })
    }
  },
  created() {
    this.fetchAPI2()
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
