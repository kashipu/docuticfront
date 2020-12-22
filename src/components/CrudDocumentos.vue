<template>
    <div class="container">
        <div class="row">
            <div class="buttonbox col-12">
                <button type="button" class="btn btn-success" data-toggle="collapse" data-target="#collapseExample" aria-expanded="false" aria-controls="collapseExample">
                    Crear Documento</button>
            </div>
        </div>
        <div class="row my-4">
            <div class="formbox border p-4 bg-light col-12 my-2 collapse" id="collapseExample">
                <form action="https://sprint2-ciclo3-grupo-11.herokuapp.com/uploadfile/" enctype="multipart/form-data" method="post">
                    <div class="form-group">
                        <label for="formGroupExampleInput">Nombre del documento</label>
                        <input type="text" class="form-control" id="formGroupExampleInput" placeholder="Nombre">
                    </div>
                    <div class="form-group">
                        <label for="formGroupExampleInput2">Descripción del documento</label>
                        <input type="text" class="form-control" id="formGroupExampleInput2" placeholder="Descripción">
                    </div>
                        <div class="form-group">
                            <input name="file" type="file" multiple>
                        </div>
                    <button type="submit" class="btn btn-info px-5">Enviar</button>                    
                </form>
            </div>
        </div>
    </div>
</template>

<script>
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
        
    }, 
    created(){
        this.getData()
    }
}
</script>

<style>

</style>