
<template>
<div class="home_page">
<div class="container">
  <TopBar :title="topBarData"/>
  <div class="item_conatner">
    <template v-for="(item,index) in visibleCarts"  v-bind:key="item.id" >
     <LargeCartItem
     v-if="index===0 || index%10===0 || index===6"
    :itemsList="item"
    data-aos="zoom-in-up"
    data-aos-duration="800"
    data-aos-easing="ease-in-out"
     />
     <CartItem
     v-else
    :itemsList="item"
    data-aos="zoom-in-up"
    data-aos-duration="800"
    data-aos-easing="ease-in-out"
     />     
  </template>
  </div>
  <span><button @click="cartVisible += step" v-if="cartVisible < items.length">View More</button></span>
</div>
</div>
</template>

<script>
import LargeCartItem from"./components/LargeCartItem.vue";import CartItem from"./components/CartItem.vue";import TopBar from"./components/TopBar.vue";import axios from"axios";import AOS from"aos";import"aos/dist/aos.css";export default{name:"App",components:{TopBar:TopBar,LargeCartItem:LargeCartItem,CartItem:CartItem},data:()=>({topBarData:[],items:[],cartVisible:7,step:3}),mounted(){AOS.init(),axios.get("https://api.rss2json.com/v1/api.json?rss_url=http://rss.cnn.com/rss/edition.rss").then(t=>{this.topBarData=t.data.feed.title,this.items=t.data.items,console.log(t.data.items)}).catch(t=>{console.log(t)})},computed:{visibleCarts(){return this.items.slice(0,this.cartVisible)}}};
</script>

<style lang="scss">
@import url('http://fonts.cdnfonts.com/css/itc-avant-garde-pro-md');
@import "./Global.scss";
* {margin: 0 !important;font-family: 'ITC Avant Garde Pro Md', sans-serif; }
.home_page{
  padding-top:50px;
  padding-bottom: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: fit-content;
  .container{
    width: 70%;
    height: fit-content;
    overflow: auto;
    display: flex;
    flex-direction: column;
    
     @include tablet_device{
       width: 85%;
       }
    .item_conatner{
      overflow: hidden;
      display: flex;
      flex-wrap: wrap;
      flex-direction: row;
      align-items: center;
      justify-content: space-evenly;
      width: 100%;
      height: 96%;
       @include tablet_device{
       flex-direction: column;
       }
    }
    span{
      display: flex;
     justify-content: center;
      button{
        padding: 8px;
        width: 130px;
        border: 2px solid black;
        background-color: #ffffff;
        cursor: pointer;
         transition:  0.2s ease-in-out; 
        &:hover{
          font-size: 15px;
          transition:  0.2s ease-in-out;
        }
      }
    }
  }
}

</style>
