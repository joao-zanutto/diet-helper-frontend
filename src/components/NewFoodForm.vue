<template>
  <div>
    <form>
        <h1> Adicionar uma nova comida</h1>
        <input type="text" class="form-control" v-model="foodName" placeholder="Nome da Comida">
        <input type="text" class="form-control" v-model="carboCount" placeholder="g de carbo por 100g de alimento">
        <input type="text" class="form-control" v-model="protCount" placeholder="g de proteínas por 100g de alimento">
        <input type="text" class="form-control" v-model="fatCount" placeholder="g de gordura por 100g de alimento">
        <button class="btn btn-primary"> Criar Alimento </button>
    </form>
    <div class="stats">
      <h3>{{ caloriesCount }} kcal por 100g de {{ foodName }}</h3>
      <p> Peso em Macros: {{ totalWeigth }}g</p>
      <p> Carboidratos: {{ carboPercent }}%</p>
      <p> Proteinas: {{ protPercent }}%</p>
      <p> Gorduras: {{ fatPercent }}%</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NewFoodForm',
  props: {
  },
  data: function(){
    return {
      foodName: "",
      carboCount: "",
      protCount: "",
      fatCount: "",
    }
  },
  methods: {
    addFoodItem: function(){
      
    }
  },
  computed: {
    caloriesCount: function(){
      return 4*Number(this.carboCount) + 4*Number(this.protCount) + 9*Number(this.fatCount)
    },
    totalWeigth: function(){
      return Number(this.carboCount) + Number(this.protCount) + Number(this.fatCount);
    },
    carboPercent: function(){
      return ((Number(this.carboCount) / this.totalWeigth) * 100).toFixed(2)
    },
    protPercent: function(){
      return ((Number(this.protCount) / this.totalWeigth) * 100).toFixed(2)
    },
    fatPercent: function(){
      return ((Number(this.fatCount) / this.totalWeigth) * 100).toFixed(2)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
form{
  text-align: left;
  margin: 20px;
}
input{
  margin-top: 10px;
  margin-bottom: 10px;
}
.stats{
  text-align: left;
  margin-left: 20px;
}
</style>
