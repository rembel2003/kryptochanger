<script>
import Input from "@/components/input.vue";
import Selector from "@/components/Selector.vue";
import CryptoConvert from "crypto-convert";
import Favourite from "@/components/Favourite.vue";


const convert= new CryptoConvert()
export default {
  components:{Input,Selector,Favourite},
  data(){
    return{
      amount:0,
      cryptoFirst:'',
      cryptoSecond:'',
      error:'',
      result:0,
      favs:[]
    }
  },
  methods:{
    changeAmount(val){
      this.amount = val
    },
    SetCryptoFirst(val){
      this.cryptoFirst = val
    },
    SetCryptoSecond(val){
      this.cryptoSecond = val
    },
    async Convert(){
      if(this.amount <=0 ){
        this.error = "Введите корректное число"
        return
      }
      else if(this.cryptoFirst==this.cryptoSecond){
        this.error="Выберите разные валюты"
        return
      }
      this.error=""

      await convert.ready();
      if(this.cryptoFirst == 'BTC' && this.cryptoSecond == 'ETH')
        this.result=convert.BTC.ETH(this.amount)
      else if(this.cryptoFirst == 'BTC' && this.cryptoSecond == 'USDT')
        this.result=convert.BTC.USDT(this.amount)
      else if(this.cryptoFirst == 'ETH' && this.cryptoSecond == 'BTC')
        this.result=convert.ETH.BTC(this.amount)
      else if(this.cryptoFirst == 'ETH' && this.cryptoSecond == 'USDT')
        this.result=convert.ETH.USDT(this.amount)
      else if(this.cryptoFirst == 'USDT' && this.cryptoSecond == 'BTC')
        this.result=convert.USDT.BTC(this.amount)
      else if(this.cryptoFirst == 'USDT' && this.cryptoSecond == 'ETH')
        this.result=convert.USDT.ETH(this.amount)
    },
    favourite(){
      this.favs.push({
        from:this.cryptoFirst,
        to:this.cryptoSecond
      })
    },
    getFavourite(index){
      this.cryptoFirst=this.favs[index].from
      this.cryptoSecond=this.favs[index].to
    }
  }
}
</script>
<template>
  <h1>Crypto</h1>
  <Favourite :favs="favs" v-if="favs.length > 0" class="favourite" :getFavourite="getFavourite"/>
  <Input :changeAmount="changeAmount" :convert="Convert" :favourite="favourite"/>
  <p v-if="result != 0" class="result">{{result}}</p>
  <div class="selectors">
    <Selector :setCrypto="SetCryptoFirst" :cryptoNow="cryptoFirst"/>
    <Selector :setCrypto="SetCryptoSecond" :cryptoNow="cryptoSecond"/>
  </div>
  <p v-if="error != '' " class="error">{{error}}</p>
</template>
<style>
h1{
  font-family: 'Nabla',bold;
  margin-top: 100px;
  font-size: 150px;
}
.selectors{
  display: flex;
  justify-content: space-around;
  width: 700px;
  margin: 0 auto;
}
.error{
  color: #ff0000;
  font-size: 50px;
}
.result{
  color: rgba(253,187,45,1) ;
  font-size: 40px;
  font-family: 'Nabla',bold;
}
.favourite{
  position: relative;
  margin-bottom: 40px;
}
</style>