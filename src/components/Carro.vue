<template>
  <div>
    <div v-for="carr in carro" :key="carr.id" class="card mb-3" style="max-width: 540px">
        <div class="row g-0">
            <div class="col-md-4">
            <img :src="carr.url" class="img-fluid rounded-start" :alt="carr.nombre" />
            </div>
            <div class="col-md-8">
                <div class="card-body">
                    <h5 class="card-title">{{ carr.nombre }}</h5>
                    <button
                    type="button"
                    class="btn btn-danger"
                    @click="eliminar"
                    :id="carr.id"
                    >
                    eliminar
                    </button>
                </div>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "carro",
  props: ["carro", "contenedor"],

  methods: {
    eliminar(e){
            let option = e.target.id
            // console.log(option)
            const datos = this.carro.filter(item => item.id!= option )
            console.log("datos",datos)
            this.carro= datos
        }
  },
};
</script>
