<template>
  <div id="app">
    <div>
      <div class="row head shadow-sm rouded fixed-bottom">
        <p class="col-md-4"><router-link to="/" class="nav-link shadow">Nova Comida</router-link></p>
        <p class="col-md-4"><router-link to="/catalogue" class="nav-link shadow">Catálogo de Comidas</router-link></p>
        <p class="col-md-4"><router-link to="/diary" class="nav-link shadow">Diário</router-link></p>
      </div>
      <router-view class="view"></router-view>
    </div>
  </div>
</template>

<script>
import NewFoodForm from './components/NewFoodForm.vue'
import FoodCatalogue from './components/FoodCatalogue.vue'
import VueRouter from 'vue-router'

const router = new VueRouter({
  mode: 'history',
  base: __dirname,
  routes: [
    { path: '/', component: NewFoodForm },
    { path: '/catalogue', component: FoodCatalogue }
  ]
});


export default {
  router,
  name: 'App',
  components: {
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

.head{
  border-top: black 1px solid;
  padding-top: 20px;
}

.nav-link{
  margin-left: 50px;
  margin-right: 50px;
  background-color: blue;
  color: white;
  border-radius: 10px;
}

.nav-link:hover{
  color: white;

}
</style>
