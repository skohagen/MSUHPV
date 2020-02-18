<template>
  <div id="app">
   <v-app>
    <QuestionsAndAnswers/>
   </v-app>
  </div>
</template>

<script>
import QuestionsAndAnswers from "./components/QuestionsAndAnswers"
import Vue from 'vue'
import Vuetify from 'vuetify'
Vue.use(Vuetify)
export default {
  name: "App",
  components: {
    QuestionsAndAnswers
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}
.v-overlay:before{
  
}
</style>
