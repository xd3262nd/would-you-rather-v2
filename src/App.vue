<template>

  <div id="app">

    <h1>Would You Rather Quiz</h1>

    <Questions 
    v-for="question in questions" 
    v-bind:key="question.question" 
    v-bind:question="question.question"
    v-bind:id="question.id"
    v-bind:answer1="question.answer1"
    v-bind:answer2="question.answer2"
    v-on:answer="answerList">

    </Questions>
    <div v-if="choices.length">
      <h2>You Would Rather...</h2>
    <!-- <ul>
      <Answer v-bind:choice="choice"></Answer>

    </ul> -->
    <Answer v-bind:choices="choices"></Answer>


    </div>
    

  </div>
    
</template>


<script>
import Questions from "./components/Questions.vue"
import Answer from "./components/Answer.vue"

export default {
  name: "App",
  components: {
    Questions,
    Answer
  },
  data(){
    return{
      choices:[],
      check: false,
      questions: [
        {
          id:0,
          question: '...be a wizard or a superhero?',
          answer1: 'Wizard',
          answer2: 'Superhero',
        },
        {
          id:1,
          question: '...sail a boat or ride in a hang glider?',
          answer1: 'Sail a boat',
          answer2: 'Ride in a hang glider',
        },
        {
          id:2,
          question: '...be a famous inventor or a famous writer?',
          answer1: 'A famous inventor',
          answer2: 'A famous writer',
        }
      ]
    }
  },
  methods:{
    answerList(ans, id){
      
      if(this.choices.length == 0){
        this.choices.push({
        "question": id,
        "answer": ans
      })
      }else{
        let isPresent = this.choices.some(choice => choice.question == id)
        if (!isPresent){
          this.choices.push({'question': id, 'answer': ans})
        }else{
          this.choices.find(choice => choice.question == id).answer = ans
        }
 
      }
      
      }
     

  }

    

}
</script>


<style>
#app {
  font-family:monospace;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
  padding:15px;
  
}
h1{
  font-size: 30px;
  font-weight:bold;
}



</style>