<template>
<div class="container">
    <div class="view">
        <img :src="img_path">
        <h1>{{coin_type}}</h1>
    </div>
    <div class="price">
        <h1>Today's Price:  </h1>
    </div>
</div>
    
</template>

<script>
export default {
    name:'CoinDisplay',
    props:{
        coin_type:String
    },
    computed:{
        img_path(){
            return "./"+this.coin_type+".png"
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