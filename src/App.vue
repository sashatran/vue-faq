<template>
  <div id="app">
    <h2 class="title">Frequently asked questions</h2>
    <app-question-answer :qaData="jsonData"></app-question-answer>
    <app-footer></app-footer>
  </div>
</template>

<script>
import QuestionAnswer from './components/QuestionAnswer.vue';
import Footer from './components/Footer.vue';
import jsonData from './assets/qa.json';

export default {
    name: 'app',
    data () {
        return {
        jsonData,
        msg: 'Welcome to Your Vue.js App'
        }
    },
    components: {
        appQuestionAnswer: QuestionAnswer,
        appFooter: Footer
    }
}
</script>

<style>

* {
    box-sizing: border-box;
}

body {
    margin: 0;
    background: #f3f3f3;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

#app {
    padding: 20px;
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    /* text-align: center; */
    color: #2c3e50;
    margin-top: 60px;
}

h1, h2 {
    font-weight: normal;
}

@media (max-width: 500px) {
    body, #app {
        width: 100%;
    } 
    #app {
        margin-top: 0; 
    }

    .title {
        text-align: center;
    }
}

</style>
