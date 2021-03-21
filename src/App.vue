<template>
<div class="container">
  <PageHeader @coin_changed="coin_changed" title="Crypto Today"></PageHeader>
  <CoinDisplay :coin_data="coin_data_json"></CoinDisplay>
</div>
 
</template>

<script>
import PageHeader from './components/header.vue'
import CoinDisplay from './components/coin_display.vue'
import axios from 'axios';

export default {
  name: 'App',
  data(){
    return{
      coin_data_json:{
        "coin":"BitCoin",
        "rate":"..."
        }
    }
  },
  created(){
    this.coin_changed('BTC')
  },
  components:{
    PageHeader,
    CoinDisplay
  },
  methods:{
    async coin_changed(value){
      // this.coin_data_json.coin=value
      // this.coin_data_json.rate='...'
      try{
        const url = 'https://rest.coinapi.io/v1/assets/'+value
        const response = await axios.get(url,{
          headers:{
            'Content-Type':'application/json',
            'X-CoinAPI-Key':'9BFB34D4-258A-493A-B319-352E6D9F1CE9'
          }
        })
        this.coin_data_json.coin=response.data[0].name
        this.coin_data_json.rate=response.data[0].price_usd.toFixed(3)
      }
      catch(e){
        console.log(e)
        if(e.response){
          if(e.response.stats == 429){
            this.coin_data_json.rate="Too Many Req!"
          }
        }
      }
        
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

</style>
