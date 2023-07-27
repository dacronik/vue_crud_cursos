<template>
    <div>
        <div>
            <v-row justify="center" class="mt-8">
                <v-btn color="blue">Agregar Curso</v-btn>
            </v-row>
        </div>
        <div>
            <div>
                <tabla-cursos :cursos="cursos"/>
            </div>
        </div>
    </div>
</template>

<script>
import TablaCursos from '@/components/TablaCursos.vue';
import { mapState } from 'vuex';
export default {
    name: 'Admin-View',
    // props: {},
    data: function(){
        return {}
    },
    computed: {
        ...mapState(['cursos'])
    },
    //methods: {}
    // watch: {},
    components: {
        'tabla-cursos':TablaCursos
    },
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
}
</script>

<style scoped>
    
</style>