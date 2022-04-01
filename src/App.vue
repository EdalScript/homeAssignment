<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <ApiComponent />
</template>

<script>
import ApiComponent from './components/ApiComponent.vue'

export default {
  name: 'App',
  components: {
    ApiComponent
  }
}
</script>

<style>
#app {
  font-family: 'Inter Regular', Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
@font-face{
    font-family: 'Inter Regular';
    src: url('assets/font/Inter-Regular.otf');
}
</style>
