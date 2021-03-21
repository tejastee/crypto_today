<template>
<div>
<div id="header">
     <a href="" class="active">{{title}}</a>
     <img src="../assets/logo.png" alt="">
     <a href="" id="left">About</a>
     
</div>
<div id="coins">
    <div v-for="coin in coinlist" :key="coin.name" id="coin" v-on:click="emit_coin(coin.id)">{{coin.name}}</div>
</div>
</div>
</template>

<script>
export default {
    name:'PageHeader',
    props:{
        title:String
    },
    data(){
        return {
            // coinlist: ["BTC", "ETH", "LTC","USDT"]
            coinlist:[
                {name:'Bitcoin',id:'BTC'},
                {name:'Ethereum',id:'ETH'},
                {name:'Litecoin', id:'LTC'},
                {name:'Tether',id:'USDT'},
                {name:'Dogecoin',id:'DOGE'}
            ]
        }
    },
    methods:{
        emit_coin(coinType){
            this.$emit('coin_changed',coinType)
        }
    }
}
</script>

<style scoped>
img{
    height:25px;
    float:right;
    padding: 10px;
}
#left{
    float: right;
}
a{
  float: left;
  display: block;
  color: #f2f2f2;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
  font-size: 25px;
  font-weight: bold;
}
a:hover{
    background-color: #ddd;
    color: black;
}
#header{
    background-color: #333;
    overflow: hidden;
}
#coins{
    display: flex;
    align-items: center;
    background-color: #333;
    /* background-color:  gray; */
    
}
#coin{
    display: block;
    padding: 10px;
    color: #f2f2f2;
    font-family: Arial, Helvetica, sans-serif;
    cursor: pointer
}
#coin:hover{
    background-color: #ddd;
    color: black;
}

</style>
