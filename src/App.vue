<template>
  <!-- <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div> -->
  <div>
    <h2>
      Translate Application
    </h2>
    <TranslateForm v-on:translatedText="getResult"></TranslateForm> //v-on:子组件发送的事件=本组件中定义的方法
    <!-- <TranslateResult></TranslateResult> -->
    <h5>{{translatedText}}</h5>//占位，需要在data中声明
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import TranslateForm from './components/TranslateForm.vue'
// import TranslateResult from './components/TranslateResult.vue'

export default {
  name: 'App',
  data: function() {
    return {
      translatedText: ""
    }
  },
  components: {
    // HelloWorld
    TranslateForm
    // TranslateResult
  },
  methods: {
    getResult: function(result) {
      console.log(result)
      this.translatedText = result
      // alert(result)
    }
  }
}
</script>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
