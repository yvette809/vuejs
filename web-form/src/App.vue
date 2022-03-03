<template>
 <h1>i am getting there</h1>
 <Register/>
</template>

<script>
 import Register from './components/Register.vue'


export default {
  name: 'App',
  components: {
    Register
   
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
body{
  margin:0;
  background:#eee
}
</style>
