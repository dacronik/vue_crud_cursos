<template>
    <v-container>
        <v-table fixed-header height="400px">
            <thead>
                <tr>
                    <th class="text-left">
                        Curso
                    </th>
                    <th class="text-left">
                        Cupos                        
                    </th>
                    <th class="text-left">
                        Inscritos                       
                    </th>
                    <th class="text-left">
                        Duración                    
                    </th>
                    <th class="text-left">
                        Costo                        
                    </th>
                    <th class="text-left">
                        Terminado                        
                    </th>
                    <th class="text-left">
                        Fechas                        
                    </th>
                    <th class="text-left">
                        acciones                       
                    </th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="curso in listaCursos" :key="curso.id">
                    <td>{{ curso.nombre }}</td>
                    <td>{{ curso.cupos }}</td>
                    <td>{{ curso.inscritos }}</td>
                    <td>{{ curso.duracion }}</td>
                    <td class="text-center"><p class="bg-green rounded-pill pa-2">${{ curso.costo.toLocaleString('es-CL') }}</p></td>
                    <td v-if="curso.completado == true" class="text-center px-10"><p class="bg-info rounded-pill">Si</p></td>
                    <td v-else class="text-center px-10"><p class="bg-blue-grey-lighten-2 rounded-pill">No</p></td>
                    <td class="text-center"><p class="bg-green rounded-pill pa-2">{{ curso.fecha_registro }}</p></td>
                    <td>
                        <div class="d-flex justify-space-around">
                            <v-icon color="yellow" @click="editarCurso(curso.id)">mdi-pencil</v-icon>
                            <v-icon color="red" @click="eliminarCurso(curso.id)">mdi-delete</v-icon>
                        </div>
                    </td>
                </tr>
            </tbody>
        </v-table>
    </v-container>
</template>

<script>
export default {
    name: 'tabla-curso-comp',
    props: {
        listaCursos:{
            type:Object,
            required:true
        }
    },
    data: function () {
         return {
         }
     },
    // computed: {},
    methods: {
        eliminarCurso(id){
                this.$emit('eliminarCurso',id);
            },
        editarCurso(id){
            this.$emit('editarCurso',id);
        }
    },
        
}

    
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods

</script>

<style scoped></style>