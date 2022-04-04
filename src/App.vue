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
  font-family: 'Inter Medium', Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
@font-face{
    font-family: 'Inter Medium';
    src: url('assets/fonts/Inter-Medium.otf');
}
</style>
