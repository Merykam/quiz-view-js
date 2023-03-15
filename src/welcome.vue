<script setup>
import './assets/style.css';
</script>

<script>
export default {

            props: {
            welcomee: {
            type: Function,
            required: true
                }
}
}
    
        
    


</script>


<template>

 

<div class="container0">

<div id="home" class="flex-center1  ">
   
    

        
        <h1 class="title1">QuiZiZy</h1>

        <input class="inpText" placeholder="Enter your name" type="text">
        
            
        <input @click="welcomee()" class="inpSubmit" type="button" value="Start playing">
 



</div>

</div>








</template>

<style>


</style>
