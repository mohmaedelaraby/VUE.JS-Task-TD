<template>
    <div class="cart">
        <div class="cart_container">
            <img :src="itemsList.enclosure.link"  class="item_img" />
            <div class="info">
                <div class="info_txt">
                    <span class="txt_container"><h5>{{itemsList.title}}</h5></span>
                    <p>{{itemsList.pubDate}}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name:"CartItem",
        props:{
          itemsList : Object ,
        }
    }
</script>

<style lang="scss" scoped>
.cart{    
     //width: 31%;
    height: 290px;
     flex: 0 0 31%;
     padding-bottom:20px ;
    display: flex;
    justify-content: center;
    align-items: center;
   
    .cart_container{
        position: relative;
        width: 100%;
        height: 100%;
        
        .item_img{
            height: 100%;
            width: 100%;
        }
        .info{
            position: absolute;
            width: 100%;
            height: 100%;
            background:linear-gradient(to bottom,rgba(255, 255, 255, 0.1), rgba(0, 0, 0, 0.95));
            top: 0;
            left: 0;
            display: flex;
    align-items: center;
    justify-content: center;
            .info_txt{
                position: absolute;
                bottom: 20px;
                width: 95%;

                .txt_container{    
                    overflow: hidden;
                    width: 100%;
                    display: -webkit-box;
                    -webkit-line-clamp: 1;
                    -webkit-box-orient: vertical;

                    h5{
                    color: white;
                    font-weight: 500;
                    font-size: 32px;
                    }
                }
                p{
                    color: gray;
                    font-weight: 500;
                }
            }
        }
    }
}

</style>