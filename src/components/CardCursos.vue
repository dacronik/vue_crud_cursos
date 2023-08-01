<template>
     <v-container>
    <v-row justify="space-around">
      <v-card width="400">
       
        <v-img
        min-height="300"
        min-width="300"
        :src="curso.img"
        class="text-white"
        >
        </v-img>
       

        <v-card-text>
          <div class="font-weight-bold ms-1 mb-2 title">
            {{ curso.nombre }}
          </div>

          <v-timeline density="compact" align="start">
            <v-timeline-item
              size="x-small"
              :dot-color="colors[0]"
            >
              <div class="mb-4">
                <div class="font-weight-normal">
                    Costo: <strong>${{ curso.costo.toLocaleString('es-CL') }}</strong>
                </div>
                <div>Duracion: {{ curso.duracion }}</div>
              </div>
            </v-timeline-item>

            <v-timeline-item
              size="x-small"
              :dot-color="colors[1]"
            >
              <div class="mb-4">
                <div class="font-weight-normal">
                    Cupos: <strong>{{ curso.cupos }}</strong>
                </div>
                <div>Completado: {{ curso.completado }}</div>
              </div>
            </v-timeline-item>

            <v-timeline-item
              size="x-small"
              :dot-color="colors[0]"
            >
              <div class="mb-4">
                <div class="font-weight-normal">
                  Fecha de Resgistro:
                </div>
                <div>{{ curso.fecha_registro }}</div>
              </div>
            </v-timeline-item>

            <v-timeline-item
              size="x-small"
              :dot-color="colors[1]"
            >
              <div class="mb-4">
                <div class="font-weight-normal">
                  Descripción:
                </div>
                <div>{{ curso.descripcion }}</div>
              </div>
            </v-timeline-item>

          </v-timeline>
        </v-card-text>
      </v-card>
    </v-row>
  </v-container>
</template>

<script>

export default {
    name: 'card-cursos-compt',
    props: {
        curso:{
            type: Object,
            required: true
        }
    },
    data: function(){
        return {
            colors:['deep-purple-lighten-1','green']
        }
    },
    computed: {
      
    },
    //methods: {}
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
}
</script>

<style scoped>
  
</style>