<template>
  <div class="container">
      <div class="lead">
          <h2>Documentos</h2>
      </div>
    <div class="row">
        <div class="doculist">
            <div class="card m-3" v-for="(value, index) in datos">
                <img src="https://via.placeholder.com/300x200" class="card-img-top" alt="">
                <div class="card-body">
                    <h5 class="card-title">{{ value.title }} </h5>
                    <p class="card-text">{{ value.body}}</p>
                    <p>{{ value.id}}</p>
                    <p>{{ value.type }}</p>
                    <p>{{ value.size }}</p>
                    <div>
                        <a href="#" class="btn ml-0 btn-sm btn-warning">Editar</a>
                        <a href="#" class="btn mx-2 btn-sm btn-danger">Eliminar</a>
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
            let data = await axios.get('https://jsonplaceholder.typicode.com/posts')
            console.log(data.data[0])
            this.datos = await data.data
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

</style>
