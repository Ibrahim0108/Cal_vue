<template>
 <div class="calc">

  <div class="screen">{{ screen }}</div>
  <div class="btn clear" @click="clear()">C</div>
  <div class="btn equal" @click="equal()">=</div>

  <div class="btn num" @click="concatNum('1')">1</div>
  <div class="btn num" @click="concatNum('2')">2</div>
  <div class="btn" @click="concatOp('+')">+</div>

  <div class="btn num" @click="concatNum('3')">3</div>
  <div class="btn num" @click="concatNum('4')">4</div>
  <div class="btn" @click="concatOp('-')">-</div>

  <div class="btn num" @click="concatNum('5')">5</div>
  <div class="btn num" @click="concatNum('6')">6</div>
  <div class="btn" @click="concatOp('*')">*</div>

  <div class="btn num" @click="concatNum('7')">7</div>
  <div class="btn num" @click="concatNum('8')">8</div>
  <div class="btn" @click="concatOp('/')">/</div>

  <div class="btn num" @click="concatNum('9')">9</div>
  <div class="btn num" @click="concatNum('0')">0</div>
  <div class="btn" @click="concatNum('.')">.</div>
 </div>
</template>


<script>
import { ref } from 'vue'
export default{
 setup(){
   let screen = ref(0)
   const concatNum = (num) => {
         screen.value === 0? screen.value = num : screen.value += num;
   }

   const concatOp = (op) => {
    if(screen.value === 0 || screen.value === '.'){
      if(op == '-'){
        screen.value = op
        return
      }else {
        return
      }
    }
    screen.value += op
   }

   function clear(){screen.value = 0}

   function equal(){
    screen.value = eval(screen.value)

   }
  return {clear ,equal,concatNum ,screen,concatOp}
 }
}
</script>



<style scoped>
.calc{
  font-weight: bold;
  border: 2px solid black;
  width: 400px;
  margin: 0 auto;
  border-radius: 5px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
.screen{
  width: 100%;
  background-color: black;
  color: yellowgreen;
  text-align: right;
  font-size: 30px;
  padding: 15px;
}

.btn{
  width: 24%;
  text-align: center;
  color: rgb(10, 10, 10);
  background-color: rgb(160, 158, 158);
  border-radius: 10%;
  cursor: pointer;
  margin: 5px;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-content: center;
  padding-top: 5px;
  padding-bottom: 5px;
}
.btn:hover{
  filter: brightness(85%);
}
.btn.clear{
   background-color: red;
   border-radius: 10px;
   width: 40%;
}
.btn.equal{
   background-color: rgb(51, 85, 173);
   border-radius: 10px;
   width: 40%;
}
</style>
