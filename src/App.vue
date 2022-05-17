<template>
<div class="w-full flex">
    <div class="m-auto">
    
  <h1>Available heros: {{heroscount }}</h1>
  
  <ul>
    <li v-for="(hero,index) in dcheros " :key="index">
    
    <div>{{ hero.name }} <button @click="remove(index)">x</button></div>
    </li>  
  </ul>
  <form @submit.prevent="addheros">
  <input  v-model ="newhero" placeholder="Type hero name here"/>  
 <button type="submit">Add Hero</button>
</form>
</div>
</div>
</template>



<script>   
export default {  
    computed:{
        heroscount(){
            return this.dcheros.length;
        },
       
    }, 
   

    methods:{
        addheros(){
            if(this.newhero !==""){
            this.dcheros.push( {name: this.newhero }); this.newhero = '';
            }
            
        },      
         remove(index){
      this.dcheros = this.dcheros.filter((hero,i) => i != index)


    },
    },
    data(){
        return{
          
            newhero:"", 
            dcheros:[
             
            ]

        }
        
    }

    
 
}
</script>

<style>

</style>