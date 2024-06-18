<template>
  <div id="app">
    <!-- <TimeLineMobile/> -->
     <HolaPapa/>
  </div>
</template>

<script>
import HolaPapa from './components/HolaPapa.vue'
//  import TimeLineMobile from "./components/TimeLineMobile.vue"



export default {
  
  name: 'App',
  components: {
    // TimeLineMobile
    HolaPapa
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
