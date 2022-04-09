<template>
<div class="home_page">
<div class="container">
  <TopBar :title="topBarData"/>
  <div class="item_conatner">
    <CartItem 
    v-for="item in visibleCarts"
    v-bind:key="item.id"
    :itemsList="item"
     />
   
  </div>
  <span><button @click="cartVisible += step" v-if="cartVisible < items.length">View More</button></span>
</div>
</div>
</template>

<script>
import CartItem from './components/CartItem.vue'
import TopBar from './components/TopBar.vue'
import axios from 'axios'
export default {
  name: 'App',
  components: {
     TopBar, CartItem
  },
  data(){
    return{
      topBarData :[],
      items:[],
      cartVisible: 7,
      step: 3
    }
  },
  mounted(){
    axios.get('https://api.rss2json.com/v1/api.json?rss_url=http://rss.cnn.com/rss/edition.rss')
      .then((res)=>{
        this.topBarData=res.data.feed.title
        this.items=res.data.items
        console.log(res.data.items)})
      .catch((err)=>{console.log(err)})
  },
  computed:{
     visibleCarts() {
      return this.items.slice(0, this.cartVisible)
    }
  }
}
</script>

<style lang="scss">
@import url('http://fonts.cdnfonts.com/css/itc-avant-garde-pro-md');
* {margin: 0 !important;font-family: 'ITC Avant Garde Pro Md', sans-serif; }
.home_page{
  background-color: red;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: fit-content;
  .container{
    background-color: white;
    width: 90%;
    height: 90%;
    .item_conatner{
      width: 100%;
      height: 96%;
      background-color: aqua;
      display: flex;
      flex-direction: row;
      flex-wrap: wrap;
      justify-content: space-evenly;
    }

    span{
      display: flex;
     justify-content: center;
      button{
        padding: 8px;
        width: 130px;
        border: 2px solid black;
        background-color: #ffffff;

      }
    }
  }
}

</style>
