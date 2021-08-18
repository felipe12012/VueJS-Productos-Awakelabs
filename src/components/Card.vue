<template>
<div class="row">
    <div id="card" v-for="cont in this.contenedor" :key="cont.id" class="col-4" >
            <img class="img-fluid" :src="cont.url" :alt="cont.nombre" />
            <h3>{{cont.nombre}}</h3>
            <p>{{cont.cantidad}}</p>
            <button type="button" :id="cont.id" class="btn btn-outline-success" @click="agregarCarrito">Agregar</button>
        </div>
</div>
</template>

<script>
export default {
    name:"Card",
    props:["contenedor","carrito"],
    methods: {
    agregarCarrito(e){
    
            this.carrito(e)
        }
    },
}
</script>