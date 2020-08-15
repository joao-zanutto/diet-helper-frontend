<template>
    <div class="diary">
        <h1> Diário </h1>
        <div class="input">
            <div class="row">
                <div class="col-md-3">
                    <input class="form-control shadow-sm" type="number" placeholder="Peso">
                </div>
                <div class="col-md-3">
                    <input class="form-control shadow-sm" type="number" placeholder="g/kg Carbo">
                </div>
                <div class="col-md-3">
                    <input class="form-control shadow-sm" type="number" placeholder="g/kg Prot">
                </div>
                <div class="col-md-3">
                    <input class="form-control shadow-sm" type="number" placeholder="g/kg Gordura">
                </div>
            </div>
            <div class="row">
                <div class="col-md-3">
                    <button class="btn btn-success"> Salvar Dados </button>
                </div>
            </div>
        </div>
        <h2> Progresso Diário  </h2>
        <div>

        </div>
    </div>
</template>

<script>
export default {
    name: 'Diary',
    data: function (){
        return{

        };
    },
    methods: {
        
    },
}
</script>

<style scoped>
.row{
    margin-top: 10px;
}

.diary{
    text-align: left;
}

h2{
    margin-top: 30px;
}
</style>