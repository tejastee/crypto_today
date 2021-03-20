<template>
<div class="container">
  <PageHeader @coin_changed="coin_changed" title="Crypto Today"></PageHeader>
  <CoinDisplay :coin_type="current_coin"></CoinDisplay>
</div>
 
</template>

<script>
import PageHeader from './components/header.vue'
import CoinDisplay from './components/coin_display.vue'

export default {
  name: 'App',
  data(){
    return{
      current_coin:"BitCoin"
    }
  },
  components:{
    PageHeader,
    CoinDisplay
  },
  methods:{
    coin_changed(value){
        this.current_coin=value
    }
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

.container {
  
}
</style>
