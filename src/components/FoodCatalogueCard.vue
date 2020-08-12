<template>
    <div class="card" style="width: 18rem;">
         <div class="card-body">
            <h5 class="card-title"> {{food.name}} </h5>
            <h6 class="card-subtitle mb-2 text-muted"> {{food.quanti}}</h6>
            <div class="mt-auto">
                <p class="card-text">Carbo: {{food.carboCount}}g</p>
                <p class="card-text">Proteinas: {{food.protCount}}g</p>
                <p class="card-text">Gorduras: {{food.fatCount}}g</p>
            </div>
        </div>
        <button class="btn btn-danger" @click="deleteFood"> Deletar </button>
    </div>
</template>

<script>
export default {
    name: 'FoodCatalogueCard',
    props:{
        food: Object,
    },
    methods: {
        deleteFood: function(){
            var component = this;

            fetch('http://localhost:3000/foods/' + this.food._id, {
                method: 'DELETE',
                headers: {
                    'Content-Type': 'application/json',
                },
            })
            .then(res => res.text())          // convert to plain text
            .then(text => console.log(text))
            .then( () => component.$emit('deleted'))
            .catch((error) => {
                console.error('Error:', error);
            });
        }
    }
}
</script>

<style>

</style>