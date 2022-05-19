<template>
    <div class="flex justify-center">
        <div>
            <h1 class="text-2xl text-center">Vue calender</h1>
        
             <section class="mx-2  flex justify-between">
              <h2 class="font-bold">{{currentmonthname}}</h2> 
             <h3 class="font-bold">{{currentYear}}</h3>
              
             </section>
             
            <section class="flex my-3"> 
                <p   class=" text-center " style="width:14.28%" v-for="day in days" :key="day">{{ day }}</p>   
            </section>
            <section class="flex flex-wrap ">
              <p    class=" text-center" style="width: 14.28%" v-for="num in startDay ()" :key="num"></p>
              <p    class=" text-center" style="width: 14.28%" v-for="num in daysInMonth ()" :key="num"   
                :class="currentdateclass(num)">{{ num }}</p>
               
            </section>
            <section class="flex justify-between my-4">
              <button class="px-2 border rounded" @click="prev">Prev</button>
               <button class="px-2 border rounded" @click="next" >Next </button>
            </section>
        </div>
    </div>

 </template>

<script>
import { computed } from '@vue/runtime-core';
export default { 
    data(){
        return{
            currentdate: new Date().getUTCDate(),
            currentmonth: new Date().getMonth() ,
            currentmonthname: new Date().toLocaleString("deflaut",{month:"long"}),
            currentYear: new Date().getFullYear(),
            days:[
                "Sun","Mon","Tue","Wed","Thu", "Fri","Sat"
            ],
        }  
                
    },  
   
 methods:{
     daysInMonth(year, month)
     {
        return new Date(this.currentYear, this.currentmonth +1, 0).getDate();
        },
     startDay(){
         return new Date(this.currentYear, this.currentmonth,1).getDay();
     },
    
      
      next(){
          if(this.currentmonth == 11){
              this.currentmonth = 0;
              this.currentYear++;
            }
            else{this.currentmonth++;
              }
          
      },

      
      prev(){
          if(this.currentmonth == 0){
              this.currentmonth = 11;
              this.currentYear--;
            }
          else{this.currentmonth--;}
          
      },

     currentdateclass(num){
         const calenderFulldate = new Date(this.currentYear,this.currentmonth,num).toDateString();
         const currentfulldate = new Date().toDateString();
        return calenderFulldate == currentfulldate ? "text-yellow-600" : ""; 

     }


     },
 
   computed:{
       currentmonthname() {
       return new Date(this.currentYear, this.currentmonth).toLocaleString("deflaut",{month:"long"});
    
       }
      
   }
}







</script>

<style>

</style>