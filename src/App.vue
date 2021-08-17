<template>
  <div id="app">
    <headers />
    
    <div class="container-fluid">
            <div class="row text-center">
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
                    <button class="btn btn-outline-success btn-lg" type="button" @click="agregarProducto">Agregar</button>
                </form>

              
                <div class="row col-6 d-flex justify-content-between">
                    <h2 class="far fas fa-check-square fa-2x "></h2>
                    <h4 class="font-weight-bold text-center">Opciones de Productos</h4>
                    <!-- <div v-for="cont of contenedor" :key="cont.id" class="card col-4 ">
                        <img class="img-fluid" :src="cont.url" />
                        <h3>{{cont.nombre}}</h3>
                        <p>{{cont.cantidad}}</p>
                    </div> -->
                    <productos

                        :contenedor="contenedor"
                        :carro="carro"
                    ></productos>
                </div>
                <div class="col-3 ">
                    <h2 class="far fas fa-shopping-basket fa-2x "></h2>
                    <h4 class="font-weight-bold text-center">Productos Agregados </h4>
                    <div class="sidebar">
                        <carrito
                            :carro="carro"
                            :contenedor="contenedor"
                        ></carrito>
                    </div>
                    <!-- <div class="card" v-for="carr of carrito">
                        <img :src="carr.url" class="img-fluid" alt="">
                        <h1>{{carr.nombre}}</h1>
                    </div> -->
                    
                </div>
            </div>
        </div>
      <footers />  
  </div>
</template>

<script>
import headers from "./components/Header.vue";
import footers from "./components/Footer.vue";
import productos from "./components/Productos.vue";
import carrito from "./components/Carro.vue"

export default {
  name: "App",
  components: {
    headers,
    footers,
    productos,
    carrito
  },
  data() {
    
    return {
        nombre:'',
        cantidad:'',
        url:'',
        contenedor:[{
            id:1,
            nombre:'Frutillas',
            cantidad: 10,
            url:'https://picsum.photos/id/1080/200/300'
        },
        {
            id:2,
            nombre:'Cebollas',
            cantidad:3,
            url:'https://picsum.photos/id/292/200/300'
        },
        {
            id:3,
            nombre:'Café en grano',
            cantidad:5,
            url:'https://picsum.photos/id/766/200/300'
        }],
        nuevoProducto:null,
        carro:[]
    }
    
  },
  methods: {
    agregarProducto(){
            let producto= {
                id: this.contenedor.length+1,
                nombre : this.nombre,
                cantidad: this.cantidad,
                url: this.url
            }
            console.log(this.contenedor.length)
            this.contenedor.push(producto)
        }
  },
};

</script>

<style>

body {
    margin: 0;
    font-family: 'Raleway', sans-serif;
}

.sidebar{
    /* position: fixed;
    right: 0; */
    max-height: calc(100vh - 6rem);
    overflow-y: auto;
    background-color: #e6e3e3;
}

h1{
    font-weight:bold;
    font-size: 3rem;
    text-align: center;
    color:white;
    padding-top: 20px;
    padding-bottom: 10px;
    }

    .header {
        background-color: #00224b;
        font-family: 'Raleway', sans-serif;
        text-align: center;
        margin-bottom: 100px;
        height: 240px;
    }


    h2{
        margin-top: 10px;
        align-items: center;
        color: #77808b;
        }

    h6{
        margin-top: 50px;
        padding-bottom: 10px;
        align-items: center;
        color:  white;
        }
    
    h4{
    font-weight:bold;
    font-size: 1,5rem;
    text-align: center;
    color: #0b51a7;
    padding-top: 10px;
    padding-bottom: 20px;
    }
    

 h3{
    font-size: 1.5rem;
    text-align: center;
    color:  #77808b;
    padding-top: 5px;
    padding-bottom: 20px;
    }
</style>
