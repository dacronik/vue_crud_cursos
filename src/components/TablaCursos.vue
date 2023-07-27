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
                <tr v-for="curso in cursos" :key="curso.id">
                    <td>{{ curso.nombre }}</td>
                    <td>{{ curso.cupos }}</td>
                    <td>{{ curso.inscritos }}</td>
                    <td>{{ curso.duracion }}</td>
                    <td class="bg-green">${{ curso.costo }}</td>
                    <td v-if="curso.completado == true">Sí</td>
                    <td v-else>No</td>
                    <td>{{ curso.fecha_registro }}</td>
                    <td>
                        <v-icon color="yellow">mdi-pencil</v-icon>
                        <v-icon color="red">mdi-delete</v-icon>
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
        cursos:{
            type:Object,
            required:true
        }
    },
    data: function () {
        return {
        }
    },
    computed: {
        },
    methods: {
        
    }

    
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
}
</script>

<style scoped></style>