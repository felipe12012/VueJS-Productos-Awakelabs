<template>
    <div class="row">
        <!-- <div id="productos" v-for="cont in contenedor" :key="cont.id" class="card col-4 ">
            <img class="img-fluid" :src="cont.url" :alt="cont.nombre" />
            <h3>{{cont.nombre}}</h3>
            <p>{{cont.cantidad}}</p>
            <button type="button" :id="cont.id" class="btn btn-outline-success" @click="carrito">Agregar</button>
        </div> -->
        <!-- <div v-for="cont in contenedor" :key="cont.id" >
        <Card 
            :nombre="cont.nombre"
            :cantidad="cont.cantidad"
            :url ="cont.url"
        ></Card>

        </div> -->
        <Card :contenedor="contenedor" :carrito="carrito" />
    </div> 
</template>

<script>
import Card from './Card.vue'

export default {
  components: { Card },
    name: 'productos',
    props:["contenedor","carro"],
    component:
        Card
    ,
    methods:{
        carrito(e){
            let option = e.target.id
            console.log(this.contenedor)
            const datos = this.contenedor.filter(item => item.id== option )
            console.log(datos)
            this.carro.push(datos[0])
            
        },
        
    }
}


</script>


