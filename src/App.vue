<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
<!--  <Ref :range='state.range'/>-->
  <RefAndToRef />
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
// import Ref from './components/ref';
import RefAndToRef from './components/ref-toRef';
import { reactive } from 'vue';
export default {
  name: 'App',
  components: {
    HelloWorld,
    // Ref,
    RefAndToRef
  },
  setup() {
    const state = reactive({
      range: 5
    });
    return {
      state
    }
  },
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
