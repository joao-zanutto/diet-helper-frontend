<template>
    <div id="catalogue">
        <h1>Catalogo de Comidas</h1>
        <div class="row catalogue">
            <FoodCatalogueCard @deleted="fetchFoods" class="foodElement shadow-sm" v-for="food in foodList" :key="food._id" :food="food" />
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
    created (){
        this.fetchFoods();
    }
}
</script>

<style>
#catalogue{
    text-align: left;
}

.catalogue{
    margin-left: 50%;
}

.foodElement{
    margin-left: 10px;
    margin-top: 10px;
}
</style>