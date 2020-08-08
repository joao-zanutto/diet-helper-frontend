<template>
    <div id="catalogue">
        <button class="btn btn-primary" @click="fetchFoods"> Atualizar</button>
        <h1>Catalogo de Comidas</h1>
        <div class="row">
            <FoodCatalogueCard v-for="food in foodList" :key="food" :food="food"/>
        </div>
    </div>
</template>

<script>
import FoodCatalogueCard from './FoodCatalogueCard'

export default {
    name: 'FoodCatalogue',
    components: {
        FoodCatalogueCard
    },
    data: function (){
        return {
            foodList: [],
        };
    },
    methods: {
        fetchFoods: function(){
            fetch('http://localhost:3000/foods')
            .then(response => response.json())
            .then(data => this.foodList = data)
            .catch(function (error) {
                alert(error);
            })
        }
    },
}
</script>

<style>
#catalogue{
    text-align: left;
    margin: 20px;
    margin-top: 0px;
}

p{
    padding: 0px;
    margin: 0px;
}
</style>