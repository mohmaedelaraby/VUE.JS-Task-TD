<template>
    <div class="cart">
        <div class="cart_container">
            <img :src="itemsList.enclosure.link"  class="item_img"  />
            <div class="info">
                <div class="info_txt">
                    <span class="txt_container"><h5>{{itemsList.title}}</h5></span>
                    <p>{{slicedDate}}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>export default{name:"CartItem",data:()=>({date_:String,slicedDate:String}),props:{itemsList:Object},mounted(){if(this.date_=this.itemsList.pubDate,this.date_)this.slicedDate=this.date_.toString().slice(0,10),console.log("date",this.date_,"==>",this.slicedDate);else{var t=new Date,e=String(t.getDate()).padStart(2,"0"),a=String(t.getMonth()+1).padStart(2,"0"),i=t.getFullYear();this.slicedDate=i+"-"+a+"-"+e}}};</script>

<style lang="scss" scoped>
@import "../Global.scss";
.cart{
    width:63%;
     height: 220px;
     padding-bottom: 20px;
    display: flex;
    flex: 0 0 64%;
    justify-content: center;
    align-items: center;
    
     @include tablet_device{
       width: 100%;
    }
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
                    font-size: 20px;
                    @include mid_device{ font-size: 14px; }
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