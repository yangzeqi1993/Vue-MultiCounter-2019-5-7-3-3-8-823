<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <CounterSum msg="总数"/>
    <CounterGroup />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import CounterGroup from './components/CounterGroup.vue'
import CounterSum from './components/CounterSum.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    CounterSum,
    CounterGroup
  },
  data(){
    return {
      counterNum: 2
    }
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
