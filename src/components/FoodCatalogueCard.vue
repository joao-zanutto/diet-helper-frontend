<template>
    <div class="card" style="width: 18rem;">
         <div class="card-body">
            <h5 class="card-title"> {{food.name}} </h5>
            <h6 class="card-subtitle mb-2 text-muted"> {{food.quanti}}</h6>
            <p class="card-text">Carbo: {{food.carboCount}}g</p>
            <p class="card-text">Proteinas: {{food.protCount}}g</p>
            <p class="card-text">Gorduras: {{food.fatCount}}g</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'FoodCatalogueCard',
    props:{
        food: Object,
    }
}
</script>

<style>

</style>