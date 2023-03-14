<script setup>
import './assets/style.css';
</script>

<script>
export default {
    props:['array','falseQ']
    
        
    }


</script>


<template>

 


    <div class="container3" v-for="arra in array" >

      

    <div class="card2">
    
        <h6>Question :</h6>
        <p id="name">{{ arra.question }}</p>

        <h6>Your answer :</h6>
        <p id="AnswerUser">{{ arra.choice }}</p>

        <h6>The right answer :</h6>
        <p id="RightAnswer">{{ arra.rightAnswer }}</p>

        <h6>Explication :</h6>
        <p id="Explication">{{ arra.Explication }}</p>

   

    </div>
    </div>











</template>

<style>


</style>
