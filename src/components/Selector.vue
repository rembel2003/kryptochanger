<template>
  <ul>
    <li @click="setCrypto('BTC')" :class="cryptoNow == 'BTC'?'active':''">Bitcoin</li>
    <li @click="setCrypto('ETH')" :class="cryptoNow == 'ETH'?'active':''">ETH</li>
    <li @click="setCrypto('USDT')" :class="cryptoNow == 'USDT'?'active':''">USDT</li>
  </ul>
</template>

<script>
export default {
  name: "Selector",
  props:{
    setCrypto:{
      type: Function,
      required: true,
    },
    cryptoNow:{
      type: String,
      required: true,
    }
  },
}
</script>

<style scoped>
ul{
  list-style:none;
  width: 200px;
  padding: 0px;
  border-radius: 3px;
  border: 3px solid #000;
}
li{
  display: block;
  background: #1A032D;
  color: white;
  padding:20px 0;
}

li:hover,li.active{
  background: #24043e;
  cursor: pointer;
}
</style>