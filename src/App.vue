<template>
<section class="flex w-full">
    <div class="m-auto">
        <h1  class="text-3xl text-center font-bold"> Vue Caculator</h1>
        <p class="text-3xl text-right mt-10 mb-2 w-32  h-12 overflow-x-scroll" style="direction:ltr">{{currentNum}}</p>
        <small>{{prevNum}} {{selectedoperation}} {{currentNum}}</small>
        <div class=" grid grid-cols-4 gap-1">
        <button @click="pressed('1')"   class="p-2 w-10 h-10 border rounded shadow">1</button>
        <button @click="pressed('2')"  class="p-2 w-10 h-10 border rounded shadow">2</button>
        <button @click="pressed('3')"  class="p-2 w-10 h-10 border rounded shadow">3</button>
        <button @click="pressed('+')"  class="p-2 w-10 h-10 border rounded shadow">+</button>
        <button @click="pressed('4')"  class="p-2 w-10 h-10 border rounded shadow">4</button>
        <button @click="pressed('5')"  class="p-2 w-10 h-10 border rounded shadow">5</button>
        <button @click="pressed('6')"  class="p-2 w-10 h-10 border rounded shadow">6</button>
        <button @click="pressed('-')"  class="p-2 w-10 h-10 border rounded shadow">-</button>
        <button @click="pressed('7')"  class="p-2 w-10 h-10 border rounded shadow">7</button>
        <button @click="pressed('8')"  class="p-2 w-10 h-10 border rounded shadow">8</button>
        <button @click="pressed('9')"  class="p-2 w-10 h-10 border rounded shadow">9</button>
        <button @click="pressed('*')"  class="p-2 w-10 h-10 border rounded shadow">*</button>
        <button @click="pressed('c')"  class="p-2  h-10 border rounded shadow">C</button>
        <button @click="pressed('0')"  class="p-2  h-10 border rounded shadow">0</button>
        <button @click="pressed('=')"  class="p-2  h-10 border rounded shadow">=</button>
        <button @click="pressed('/')"  class="p-2 w-10 h-10 border rounded shadow">/</button>
        
        
 


    </div>
    </div>

    
</section>
   



</template>

<script>
import { onMounted, onUnmounted, ref } from 'vue'
export default {
 setup(){
     
     const operations = ['+','-','*','/'];
     const numbers = ['1','2','3','4','5','6','7','8','9','0'];
      const currentNum = ref("");
      const prevNum = ref(""); 
      const selectedoperation = ref("");


     function pressed(value){
         if (value == "=" || value == "Enter") calculate();  
         else if (value == 'c') clear();
         else if(operations.includes(value)) applyoperations(value);
         else if(numbers.includes(value)) appendNumber(value);
        }

      function appendNumber(value){
          currentNum.value = currentNum.value + value;
      }
         
      function applyoperations(value){
          calculate();
          prevNum.value = currentNum.value;
          currentNum.value = "";
          selectedoperation.value = value;
      }



      function calculate(){
          if(selectedoperation.value == "*") multiply();
          else if(selectedoperation.value == "+") sum();
           else if(selectedoperation.value == "-") subtract();
          else if(selectedoperation.value == "/") divide();

          prevNum.value="";
          selectedoperation.value="";
          
      }
         function multiply(){
             currentNum.value = prevNum.value * currentNum.value;
         }

          function sum(){
             currentNum.value = +prevNum.value + +currentNum.value;
         }

         function subtract(){
             currentNum.value = prevNum.value - currentNum.value;
         }

         function divide(){
             currentNum.value = prevNum.value / currentNum.value;
         }

        
      function clear(){
          currentNum.value = "";
      }




      onMounted(() => {
        window.addEventListener("keydown",(e) => {
            pressed(e.key);
            // console.log("mee");
            // let numbers = [1,2,3,4,5,6,7,8,9,0]
            // let operators = ["+", "-", "/", "*"]
            // let pressedVal = e.key
            // if(numbers.includes(pressedVal) || operators.includes(pressedVal) || pressedVal === "c" || pressedVal === "=")
                
        }); 
      })
        
        onUnmounted(() => {
            window.removeEventListener("keydown");
        })






      return {currentNum, pressed , selectedoperation, prevNum,};
     }
     
     
 
}
</script>

<style>

</style>