<template>
  <div id="app">
    <headers />
    
    <div class="container-fluid">
            <div class="row text-center">
                <formulario :contenedor="contenedor" :agregar="agregarProducto" />

                <div class="row col-6 d-flex justify-content-between">
                    <h2 class="far fas fa-check-square fa-2x "></h2>
                    <h4 class="font-weight-bold text-center">Opciones de Productos</h4>
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
import carrito from "./components/Carro.vue";
import formulario from "./components/Form.vue"

export default {
  name: "App",
  components: {
    headers,
    footers,
    productos,
    carrito,
    formulario
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
        carro:[],
        // producto:''
    }
    
  },
  methods: {
    agregarProducto(producto){
            
            console.log(this.contenedor)
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
