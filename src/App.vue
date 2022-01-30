<template>
  <div id="app">
      <Header />
      <OperatorQuiz @onBack="onBack" v-if="operator" :operator = "operator" />
      <OperatorSelector v-if="!operator" @changeOperator = "changeOperator" />

  </div>
</template>

<script>

import OperatorSelector from './components/OperatorSelector.vue'
import OperatorQuiz from './components/OperatorQuiz.vue'
import Header from './components/Header.vue'

export default {
  name: 'App',
  data(){
      return {
          operator:null
      }
  },
  methods:{
      changeOperator(operator){
          this.operator= operator
      },
      onBack(){
          this.operator = null;
      }
  },
  components:{
      OperatorSelector,
      OperatorQuiz,
      Header
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  font-size: 24px;
}

</style>
