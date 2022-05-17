<template>
<div class="m-auto">
 <h1 class="text-2xl my-2">Vue calender</h1>
<section class="flex"> 
    <p v-for="day in days" :key="day">{{ day }}</p>   
    </section>
</div>

 </template>

<script>
export default { 
    data(){
        return{
            days:[
                "Sun","Mon","Tue","Wed","Thu", "Fri","Sat"],
        }
                
    }

}
</script>

<style>

</style>