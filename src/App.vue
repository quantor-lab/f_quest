<template>
  <ExampleRequest/>
</template>

<script>
import ExampleRequest from './components/ExampleRequest.vue'

export default {
  name: 'App',
  components: {
    ExampleRequest
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
