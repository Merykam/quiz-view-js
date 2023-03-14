<script setup>
import './assets/style.css';
</script>

<script>
export default {

//     props: {
//         showA: {
//       type: Function,
//       required: true
//     }
//   },
//     props: {
//     method: { type: Function },
//     Resultscore:{
//         type:Number,
//         required:true
//     }

//   }
    props:['Resultscore'],
    emits:['send-message']
        
    }
    
   

</script>


<template>


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Result page</title>
    <link rel="stylesheet" href="main.css">
</head>
<body>
    

    <div class="container2">

        
        <div class="card">

            <!-- <div class="centerMsg">
                <h3 id="user">Score</h3>

            </div> -->
            <div class="scor">
                <span id="Mark"> {{ Resultscore }} / 100</span>
                
            </div>
        
            
           
            <h5 id="msgSucc">You have finished your quiz</h5>
            <div class="btnResult">
                <!-- <a href="" @click="this.$emit('send-message')">Check your answers</a> -->
                <button @click="this.$emit('send-message')">Check your answers</button>

            </div>

            
   

        </div>
        



    </div>


 


    
</body>
</html>

</template>

<style>


</style>
