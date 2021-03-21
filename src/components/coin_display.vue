<template>
<div class="container">
    <div class="view">
        <img :src="img_path" alt="Coin">
        <h1>{{coin_data.coin}}</h1>
    </div>
    <div class="price">
        <h1>Today's Price: {{coin_data.rate}} $ </h1>
    </div>
</div>
    
</template>

<script>
export default {
    name:'CoinDisplay',
    props:{
        coin_data:Object
    },
    computed:{
        img_path(){
            return "./"+this.coin_data.coin+".png"
        }
    }
}
</script>

<style scoped>

.container{
    margin-top: 10px;
    padding: 30px;
    border: 2px solid black;
    border-radius: 5px;
}
.view{
    align-items: center;
    display: flex;
    justify-content: center;
}
h1{
    padding-left: 20px;
}
.price{
    text-align: center;
}

</style>