<template>
   
        <form class="col-3 ms-3">
                    <h2 class="fas fa-camera fa-2x"></h2>
                    <h4 class="font-weight-bold text-center">Agrega tu Producto</h4>
                    <div class="my-3 pr-3">
                        <label for="nombre">Nombre de producto</label>
                        <input
                            class="form-control"
                            v-model="nombre"
                            type="text"
                            name="nombre"
                            id="nombre"
                            placeholder="nombre producto"
                        />
                    </div>
                    <div class="my-3 pr-3">
                        <label for="cantidad">Cantidad</label>
                        <input
                            class="form-control"
                            v-model="cantidad"
                            type="text"
                            name="cantidad"
                            id="cantidad"
                            placeholder="Cantidad"
                        />
                    </div>
                    <div class="my-3 pr-3">
                        <label for="url">url de producto</label>
                        <input
                            class="form-control"
                            v-model="url"
                            type="text"
                            name="url"
                            id="url"
                            placeholder="Ej:https://www.images.com/image.jpg"
                        />
                    </div>
                    <button class="btn btn-outline-success btn-lg" type="button" @click="agregarDatos">Agregar</button>
                </form>
    
</template>

<script>
export default {
    name: 'formulario',
    props:["contenedor","agregar"],
    data() {
        return {
            nombre:"",
            url:"",
            cantidad:""
        }
    },
    methods: {
        agregarDatos(){
            let producto= {
                id: this.contenedor.length+1,
                nombre : this.nombre,
                cantidad: this.cantidad,
                url: this.url
            }
            // this.contenedor.push(this.producto)
            console.log(producto)
           this.agregar(producto);
            }
    },
}
    
</script>