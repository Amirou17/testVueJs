<template>
  <div id="app">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.5.3/dist/css/bootstrap.min.css" integrity="sha384-TX8t27EcRE3e/ihU7zmQxVncDAy5uIKz4rEkgIXeMed4M0jlfIDPvg6uqKI2xXr2" crossorigin="anonymous">
    <Module1 msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import Module1 from './components/Module1.vue'

export default {
  name: 'App',
  components: {
    Module1
  }
}
</script>

<style>

</style>
