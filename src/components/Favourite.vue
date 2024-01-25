<template>
  <h1 class="favs">
      Favourite
  </h1>
  <div v-for="(fav,index) in favs" :key="index" @click="getFavourite(index)">
      <p><span>{{fav.from}}</span><span>:</span><span>{{fav.to}}</span></p>
  </div>
</template>

<script>
export default {
  name: "Favourite",
  props:{
    favs:{
      type: Array,
      required: true
    },
    getFavourite: {
      type: Function,
      required: true
    }
  }
}
</script>

<style scoped>
.favs{
  font-size:40px
}
div{
  display: flex;

  justify-content: center;

}
span{
  font-family: 'Nabla', bold;
}
div:hover{
  opacity: 0.7;
  transform: scale(1.1);
  cursor: pointer;
}
</style>