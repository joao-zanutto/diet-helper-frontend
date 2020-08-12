<template>
  <div>
    <form>
        <h1> Adicionar uma nova comida</h1>
        <form>
          <input type="text" class="form-control shadow-sm" v-model="foodName" placeholder="Nome da Comida">
          <input type="text" class="form-control shadow-sm" v-model="quantity" placeholder="Quantidade da comida (un, 100g)">
          <input type="number" class="form-control shadow-sm" v-model="carboCount" placeholder="g de carbo por 100g de alimento">
          <input type="number" class="form-control shadow-sm" v-model="protCount" placeholder="g de proteínas por 100g de alimento">
          <input type="number" class="form-control shadow-sm" v-model="fatCount" placeholder="g de gordura por 100g de alimento">
          <button type="button" class="btn btn-primary shadow-sm" @click="addFoodItem"> Criar Alimento </button>
        </form>
    </form>
    <div class="stats">
      <h3>{{ caloriesCount }} kcal por {{ quantity }} de {{ foodName }}</h3>
      <p> Peso em Macros: {{ totalWeigth }}g</p>
      <p v-if="!isNaN(carboPercent)"> Carboidratos: {{ carboPercent }}%</p>
      <p v-else> Carboidratos: 0%</p>
      <p v-if="!isNaN(protPercent)"> Proteinas: {{ protPercent }}%</p>
      <p v-else> Proteinas: 0%</p>
      <p v-if="!isNaN(fatPercent)"> Gorduras: {{ fatPercent }}%</p>
      <p v-else> Gorduras: 0%</p>
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
      quantity: "",
      foodName: "",
      carboCount: "",
      protCount: "",
      fatCount: "",
    }
  },
  methods: {
    addFoodItem: function(){
      var data = {
        name: this.foodName,
        quanti: this.quantity,
        carboCount: this.carboCount,
        protCount: this.protCount,
        fatCount: this.fatCount
      }

      fetch('http://localhost:3000/foods', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify(data),
      })
      .then(response => response.json())
      .then(data => {
        console.log('Success:', data);
      })
      .catch((error) => {
        console.error('Error:', error);
      });
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
a {
  color: #42b983;
}
form{
  text-align: left;
}
input{
  margin-top: 10px;
  margin-bottom: 10px;
}
.stats{
  text-align: left;
  margin-top: 40px;
}
</style>
