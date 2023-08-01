<template>
    <v-card class="mx-auto px-6 py-8" min-width="600">
      <v-form
        v-model="form"
        @submit.prevent="onSubmit"
      >
        <v-text-field
          v-model="nombre"
          :readonly="loading"
          :rules="[required]"
          class="mb-2"
          clearable
          label="Nombre"
        ></v-text-field>

        <v-text-field
          v-model="img"
          type="text"
          :readonly="loading"
          :rules="[required]"
          clearable
          label="Url de la imagen"
          placeholder="ingrese url imagen"
        ></v-text-field>

        <v-text-field
          v-model="cupos"
          :readonly="loading"
          :rules="[required]"
          class="mb-2"
          clearable
          label="Cupos del curso"
        ></v-text-field>
        <v-text-field
          v-model="inscritos"
          :readonly="loading"
          :rules="[required,inscritosValidos]"
          class="mb-2"
          clearable
          label="inscritos en el curso"
        ></v-text-field>
        <v-text-field
          v-model="duracion"
          :readonly="loading"
          :rules="[required]"
          class="mb-2"
          clearable
          label="Duración del curso"
        ></v-text-field>
        <v-text-field
          v-model="registro"
          :readonly="loading"
          :rules="[required]"
          class="mb-2"
          clearable
          label="Fecha de Registro"
        ></v-text-field>
        <v-text-field
          v-model="costo"
          :readonly="loading"
          :rules="[required]"
          class="mb-2"
          clearable
          label="Costo del curso"
        ></v-text-field>
        <v-textarea 
        label="Descripción"
        v-model="descripcion">

        </v-textarea>

        <br>

        <div class="d-flex justify-space-around">
          <v-btn
            :disabled="!form"
            :loading="loading"
            color="success"
            type="submit"
            variant="elevated"
            >
            Crear
            </v-btn>
            <v-btn
            color="red"
            variant="elevated"
            @click="cancelarFormulario"
            >
            Cancelar
          </v-btn>
        </div>
      </v-form>
    </v-card>
</template>

<script>



export default {
    name: 'agregar-curso-form-comp',
    // props: {},
    data: function(){
        return {
            nombre: '',
            img:'',
            cupos:undefined,
            inscritos:undefined,
            duracion:'',
            registro:'',
            costo:undefined,
            completado:'false',
            descripcion:'',
            loading:false,
            form: false,
        }
    },
    computed: {
        
    },
    methods: {
        onSubmit(){
            if (!this.form)return
            this.loading = true
                this.addCurso()
        },
        required(v){
            return !!v || 'Campo es requerido'
        },
        inscritosValidos(v){
          if(parseInt(v)>this.cupos){
            return 'La cantidad de inscritos no puedes ser mayor a la cantidad de cupos disponibles'
          }
          return true;
        },
        addCurso(){
            let newCurso ={
                nombre: this.nombre,
                img: this.img,
                cupos: parseInt(this.cupos),
                duracion: this.duracion,
                inscritos: parseInt(this.inscritos),
                completado: this.completado,
                fecha_registro: this.registro,
                costo: parseInt(this.costo),
                descripcion: this.descripcion,
            }
            this.$emit('agregarCurso',newCurso)
        },
        formatoFecha(date){
            const day = date.getDate().toString().padStart(2, '0');
            const month = (date.getMonth() + 1).toString().padStart(2, '0');
            const year = date.getFullYear();
            return `${day}/${month}/${year}`;
        },
        cancelarFormulario(){
          this.$emit('cancelarFormulario')
        }
        
    },
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Method,
    beforeMount(){
        const fechaActual = new Date();
        this.registro = this.formatoFecha(fechaActual);
    }
    // -- End Lifecycle Methods
}
</script>

<style scoped>
    
</style>