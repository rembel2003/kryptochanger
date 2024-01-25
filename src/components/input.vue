<template>
<input type="number" min="0" @input="changeAmount($event.target.value)" placeholder="Введите число"></input>
  <br>
  <button @click="convert()">
      Конвертировать
  </button>
  <button @click="favourite()" class="fav-btn">
      Избранное
  </button>
</template>

<script>
export default {
  name: "input",
  props:{
    changeAmount:{
      type: Function,
      required: true
    },
    convert:{
      type: Function,
      required: true
    },
    favourite:{
      type: Function,
      required: true
    }
  }
}
</script>

<style scoped>
input{
  width: 500px;
  position: relative;
  top:0px;
  border-radius: 3px;
  border: 0;
  padding: 10px;
  background: #24043e;
  color: white;
  outline: none;
  font-family: 'Nabla', bold;
  font-size: 25px;
}
button{
  position: relative;
  margin-top: 20px;
  top:0px;
  padding: 15px 20px;
  cursor: pointer;
  background: #1A032D;
  border: 0;
  border-radius: 4px;
  color: white;
}
.fav-btn{
  margin-left: 20px;
}
</style>