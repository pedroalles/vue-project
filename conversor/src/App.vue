<template>
  <div id="app">

    <h1 class="textcenter">Currency Converter</h1>
    
    <Conversor moeda-a="USD" moeda-b="EUR"/>
   


  </div>
</template>

<script>
import Conversor from "./components/Conversor.vue";
export default {
  name: 'App',
  components: {
    Conversor
  }
}
</script>

<style>
#app {
  margin: auto;
  max-width: 340px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 50px;
}

.textcenter{
  text-align: center;
  text-shadow: 2px 5px 10px;
}
</style>
