<script setup>
import './assets/style.css';
</script>

<script>
import scoree from './Score.vue';
import result from './Result.vue';
import welcome from './welcome.vue';
export default {
  components: {scoree, result, welcome},

  data() {
        return{
          
            show:true,
            index:0,
            score:0,
            showScore:false,
            endQuestion:false,
            questionCounter:0,
            showQuestions:false,
            showAnswers:false,
            arraydata:[],
            falseQuestion:0,
            showWelcome:true,

           

      questions : [

    {
      id: 1,
        choix0 :"Why is AWS more economical than traditional data centers for applications with varying compute workloads?", 
        choix1 :"Amazon EC2 costs are billed on a monthly basis",    
        choix2 :"Users retain full administrative access to their Amazon EC2 instances.", 
        choix3 :"Amazon EC2 instances can be launched on demand when needed.", 
        choix4 :"Users can permanently run enough instances to handle peak workloads.",
        answer : 3,
        Right :"Amazon EC2 instances can be launched on demand when needed",
        Explication:"The ability to launch instances on demand when needed allows users to launch and terminate instances in response to a varying workload"
        


    },
    {
      id:2,
        choix0 :"Which AWS service would simplify the migration of a database to AWS?", 
        choix1 :"AWS Storage Gateway",    
        choix2 :"AWS Database Migration Service (AWS DMS)", 
        choix3 :"Amazon EC2", 
        choix4 :"Amazon AppStream 2.0",
        answer : 2,
        Right :"AWS Database Migration Service (AWS DMS)",
        Explication:"AWS DMS helps users migrate databases to AWS quickly and securely. The source database remains fully operational during the migration, minimizing downtime to applications that rely on the database. AWS DMS can migrate data to and from most widely used commercial and open-source databases."


    },
    {
      id:3,
        choix0 :"Which AWS offering enables users to find, buy, and immediately start using software solutions in their AWS environment?", 
        choix1 :"AWS Config",    
        choix2 :"AWS OpsWorks", 
        choix3 :"AWS SDK", 
        choix4 :"AWS Marketplace",
        answer : 4,
        Right :"AWS Marketplace",
        Explication: "AWS Marketplace is a digital catalog with thousands of software listings from independent software vendors that makes it easy to find, test, buy, and deploy software that runs on AWS."
    },
   
    {
      id:3,
        choix0 :"Which AWS offering enables users to find, buy, and immediately start using software solutions in their AWS environment?", 
        choix1 :"AWS Config",    
        choix2 :"Amazon Route 53", 
        choix3 : "AWS Direct Connect", 
        choix4 :"Amazon Virtual Private Cloud (Amazon VPC)",
        answer : 4,
        Right : "Amazon Virtual Private Cloud (Amazon VPC)",
        Explication:"Amazon VPC lets users provision a logically isolated section of the AWS Cloud where users can launch AWS resources in a virtual network that they define."


    },
    {
      id:3,
        choix0 :"Which of the following is an AWS responsibility under the AWS shared responsibility model?", 
        choix1 :"Configuring third-party applications",    
        choix2 :"Maintaining physical hardware", 
        choix3 : "Securing application access and data", 
        choix4 :"Managing guest operating systems",
        answer : 2,
        Right : "Maintaining physical hardware",
        Explication:"Maintaining physical hardware is an AWS responsibility under the AWS shared responsibility model."


    },
    {
      id:3,
        choix0 : "Which component of the AWS global infrastructure does Amazon CloudFront use to ensure low-latency delivery?", 
        choix1 : "AWS Regions",    
        choix2 :"Edge locations", 
        choix3 : "Availability Zones", 
        choix4 :"Managing guest operating systems",
        answer : 2,
        Right :"Edge locations",
        Explication:"To deliver content to users with lower latency, Amazon CloudFront uses a global network of points of presence (edge locations and regional edge caches) worldwide. "


    },




]



        }


        

  },


  methods:{

    showQ(){
      this.showWelcome=false;
      this.showQuestions=true;
      
    },
    checkanswers(){
      // e.preventDefault ();
      // this.showQuestions=false;
      this.showScore=false;
      this.showAnswers=true;
      console.log("answersssssssssssss");
    },  

    
    answerQuestion(event){

      // if(this.questions.length == this.questionCounter ){
      //   this.showQuestions=false;
      //   this.showScore=true;
      // }

     

      
      
      
      const getid=event.target.getAttribute('id');
     
     
      var i = this.index;
      

      if(getid == this.questions[i].answer){
        this.score += 10;
        console.log(this.score);
        this.questionCounter++;
        
     
       
        //   console.log('rightAnswer');
          event.target.classList.add("addGreen");

          setTimeout (()=>{
            event.target.classList.remove("addGreen");
            
         
            this.index++;
            
            if(this.questions.length == this.questionCounter ){
                this.showQuestions=false;
                this.showScore=true;
        }


           

           },2000);
          
      }else{
        this.falseQuestion++;
        console.log(this.falseQuestion);
        const choixText = this.$refs.choice.querySelector('.choix-text').textContent;
        let obj ={
          "question":this.$refs.question.textContent,
          "rightAnswer":this.questions[i].Right,
          "choice":choixText,
          "Explication":this.questions[i].Explication
        }
        this.arraydata.push(obj)
        console.log(this.arraydata);

        // const array =this.arraydata;
        
        
      
       



      
      
       
        // this.arraydata.push(event.target);
        

        this.questionCounter++;
        console.log('wrongAnswer');

        event.target.classList.add("addred");
        setTimeout (()=>{
            event.target.classList.remove("addred");
            this.index++;
            if(this.questions.length == this.questionCounter ){
        this.showQuestions=false;
        this.showScore=true;
      }

        

           

           },2000);
           console.log(this.questions[i].answer);

        
      }

 
     


    }
        
    }

};
</script>


<template>
  <div v-if="showAnswers">
    <!-- <scoree @send-message="checkanswers"/> -->
    <result :array="arraydata" :falseQ="falseQuestion"/>

  </div>
  <div v-if="showScore">
    <scoree :Resultscore="score" @send-message="checkanswers"/>
  </div>

  <div v-if="showWelcome">
    <!-- <scoree @send-message="checkanswers"/> -->
    <welcome :welcomee="showQ"/>

  </div>
  
<div class="container" v-if="showQuestions">
 
 
        <div class="flex-center"> 
            <div class="flex">
            
                <div class="question-n">
                    <p id="question-number">Question {{questionCounter+1 }} / {{questions.length}}</p>
                </div>
                <!-- <div class="progress-bar">
                    <p class="full-progress"></p>
                </div> -->
                
            </div>

          

  <div>
        <!-- {{ questions[0].choix0 }} -->


              <h1 id="gg" class="choix-text" ref="question">{{questions[index].choix0}}</h1>
         
            <div ref="choice"  id="1" v-on:click="answerQuestion" class="display-flex">
                <p id="1" class="A">A</p>
               
                <p  ref="choice" id="1" class="choix-text">{{questions[index].choix1}}</p>

            </div>
            <div ref="choice" id="2" v-on:click="answerQuestion" class="display-flex">
                <p id="2" class="A">B</p>
                <p ref="choice"  id="2" class="choix-text" >{{questions[index].choix2}}</p>

            </div>
            <div ref="choice" id="3" v-on:click="answerQuestion" class="display-flex">
                <p id="3"  class="A">C</p>
                <p ref="choice" id="3" class="choix-text">{{questions[index].choix3}}</p>

            </div>
            <div ref="choice" id="4" v-on:click="answerQuestion" class="display-flex">
                <p id="4" class="A">D</p>
                <p ref="choice" id="4" class="choix-text" >{{questions[index].choix4}}</p>

            </div> 
    </div> 


        </div>
        


    </div>



</template>

<style>


</style>
