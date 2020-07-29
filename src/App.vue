<template>
  <div id="app">
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <h1 class="text-center">The Super Quiz</h1>
      </div>
    </div>
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <component :is="mode" @answered="answered($event)" @confirmed="mode = 'app-question'"></component>
      </div>
    </div>
  </div>
</template>

<script>
import Answer from './components/Answer.vue'
import Question from "./components/Question.vue";

export default {
  name: 'App',
  data(){
    return {
      mode: 'app-question'
    }
  },
  methods: {
    answered(isCorrect) {
      if(isCorrect){
        this.mode = 'app-answer'
      } else {
        this.mode = 'app-question'
        alert('wrong answer, try again')
      }
    }
  },
  components: {
    appAnswer: Answer,
    appQuestion: Question
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
