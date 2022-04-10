<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <ApiComponent />
</template>

<script>
import ApiComponent from './components/ApiComponent.vue'
//import Dropdown from './components/Dropdown.vue'
//import DropdownContent from './components/Dropdown.vue'

export default {
  name: 'App',
  components: {
    ApiComponent,
 //   Dropdown,
 //   DropdownContent
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
