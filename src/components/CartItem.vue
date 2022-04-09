<template>
    <div class="cart">
        <div class="cart_container">
            <h1>{{itemsList.title}}</h1>
            <h2> {{itemsList.pubDate}}</h2>
            <img :src="itemsList.enclosure.link" style="height: 20px; width: 20px;"/>
        </div>
    </div>
</template>

<script>
    export default {
        name:"CartItem",
        props:{
          itemsList : Object
        }
    }
</script>

<style lang="scss" scoped>
.cart{
    width: 30%;
    height: 30%;
    display: flex;
    justify-content: center;
    align-items: center;

    .cart_container{
        position: relative;
        width: 100%;
        height: 100%;
        
        .item_img{
            position: absolute;
        }
    }
}

</style>