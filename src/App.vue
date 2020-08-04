<template>
  <div id="app">
    <NewFoodForm />
  </div>
</template>

<script>
import NewFoodForm from './components/NewFoodForm.vue'

export default {
  name: 'App',
  components: {
    NewFoodForm 
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
  margin-top: 20px;
}
</style>
