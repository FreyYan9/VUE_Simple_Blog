<template>
  <div id="app">
    <div class='logo' >
      <img src="./assets/logo.png">
      <p>Welcome to Blog</p>
    </div>
    <hr>
    <hello></hello>
  </div>
</template>

<script>
import Hello from './components/Hello'

export default {
  name: 'app',
  components: {
    Hello
  }
}
</script>

<style lang='less'>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;*/
  color: #2c3e50;
  margin-top: 60px;
  .logo{
    width: 80%;
    text-align: left;
    padding: 0 30px;
    img{
      width: 40px;
      height: auto;
      display: inline-block;
      vertical-align: middle;
    }
    p{
      display: inline-block;
      margin-left: 20px;
    }
  }
  
}
</style>
