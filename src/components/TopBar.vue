<template>
    <div>
        <ul>
             <li>
                 {{title}}
                 <hr/>
            </li>
            
        </ul>
    </div>
</template>

<script>export default{name:"TopBar",props:{title:String}};</script>

<style lang="scss" scoped>
@import "../Global.scss";
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  li {
  float: left;
  display: block;
  font-size: 18pt;
  padding-bottom: 15px;
  padding-left: 20px;
  font-weight: 500;
  color: #484848;
   @include tablet_device{
       font-size: 15pt;
       font-weight: 600;
    }
   @include large_device{
       font-size: 10pt;
       font-weight: 600;
    }
    @include mid_device{    
        font-size: 8pt;
       font-weight: 600;
    }
    
    @include small_device{    
        font-size: 7pt;
       font-weight: 800;
    }
    hr{
        width: 9%;
        background-color: #ffe50e;
        height: 5px;
        border: none;
    }
  }
}
</style>