<template>
  <div id="app">
      <hello></hello>
      <div class="casdiv" id='divls'>
        <!-- <label for="ipt">地址：</label><input type="text" id="ipt"> -->
         <div class='res'>签到</div>
       
      </div>
       <!-- <ass/> -->
  </div>
</template>

<script>
import hello from './components/HelloWorld'
import ass from './components/ass'

export default {
  name: 'App',
  components: {
    hello,
    ass
  }
}
</script>
<style>
#divls{
  margin-top: 20px;
}
#ipt{
  border: 1px solid #999;  
}
.res{
  border-radius: 50%;
  border: 1px solid #999;
  width: 100px;
  height: 100px;
  margin: auto ;
  text-align: center;
  line-height: 100px;
  
}
</style>


