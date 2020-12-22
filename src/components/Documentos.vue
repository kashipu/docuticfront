<template>
<div class="container">
    <div class="lead">
        <h2>Documentos</h2>
    </div>
    <div class="row">
        <div class="title">
            <small>
                Puede hacer la carga de archivos y ver la respuesta de la api en fastapi
                Se puede eliminar documentos, por favor recargar la página
            </small>
        </div>
        <div class="doculist">
            <div class="card m-3" v-for="(value, index) in datos">
                <img :src="value.file_img" class="card-img-top" alt="">
                <div class="card-body">
                    <h5 class="card-title">{{ value.file_name }}</h5>
                    <p>{{ value.id}}</p>
                    <p>{{ value.file_type }}</p>
                    <p>{{ value.file_size }}</p>
                    <div>
                        <a href="#" class="btn ml-0 btn-sm btn-warning">Editar</a>
                        <a @click="deleteData(value.id)" class="btn mx-2 btn-sm btn-danger">Eliminar</a>
                        <a href="#" class="btn mx-2 btn-sm btn-info">Descargar</a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<script>
    import axios from "axios"

export default {
    data() {
        return {
            datos: null
                }
    },
    methods: {
        async getData() {
            let data = await axios.get('https://sprint2-ciclo3-grupo-11.herokuapp.com/list-files')
            this.datos = await data.data
        },
        deleteData(id){
            let data = axios.delete('https://sprint2-ciclo3-grupo-11.herokuapp.com/delete/' + id)
            location.reload()
        }
    }, 
    created(){
        this.getData()
    }
}

</script>

<style>
.doculist {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
}

@media only screen and (max-width: 995px) {
.doculist {
    display: grid;
    grid-template-columns: 1fr 1fr;
}
}

@media only screen and (max-width: 767px) {
.doculist {
    display: grid;
    grid-template-columns: 1fr;
}
}


</style>
