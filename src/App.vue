<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="一如王者深似海，从此时间是路人"/>
<!--  <Ref :range='state.range'/>-->
<!--  <RefAndToRef />-->
<!--  <ToRefs/>-->
<!--  <shallowReactive />-->
<!--  <shallowRef />-->
<!--  <toRaw />-->
<!--  <markRaw />-->
  <Watch />
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
// import Ref from './components/ref';
// import RefAndToRef from './components/ref-toRef';
// import ToRefs from './components/toRefs';
// import shallowReactive from "./components/shallowReactive";
// import shallowRef from "./components/shallowRef";
// import toRaw from "./components/toRaw";
// import markRaw from "./components/markRaw";

import Watch from './components/watch';
import { reactive } from 'vue';
export default {
  name: 'App',
  components: {
    HelloWorld,
    // Ref,
    // RefAndToRef,
    // ToRefs,
    // shallowReactive,
    // shallowRef,
    // toRaw,
    // markRaw,
    Watch,

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
