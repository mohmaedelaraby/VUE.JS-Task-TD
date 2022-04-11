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
    @include cart(flex, 0 0 64%)
}
</style>