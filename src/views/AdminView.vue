<template>
    <div>
        <div>
            <v-row justify="center" class="mt-8">
                <v-btn @click="openDialog" color="blue">Agregar Curso</v-btn>
            </v-row>
        </div>
             <v-dialog
              transition="dialog-bottom-transition"
              width="auto"
              v-model="dialog"
            >
              <template v-slot>
                <v-card>
                  <v-toolbar
                    color="info"
                    :title=CursoTitle
                  ></v-toolbar>
                  <v-card-text>
                    <!--ingresando el componente form-->
                    <editar-curso v-if="showEdit" :id="idEdit" @cancelarFormulario="cerrarFormulario" @editarCurso="editarCursoById"/>
                    <form-agregar-curso v-else @agregarCurso="crearCurso" @cancelarFormulario="cerrarFormulario"/>
                    
                  </v-card-text>
                  <v-card-actions class="justify-end">

                  </v-card-actions>
                </v-card>
              </template>
            </v-dialog>
        <div>
            <div>
                <tabla-cursos :listaCursos="cursos" @eliminarCurso="deleteCurso" @editarCurso="editarCurso"/>
            </div>
            <v-dialog
                transition="dialog-bottom-transition"
                width="auto"
                v-model="dialogDelete">
               <template v-slot>
                <v-card>
                    <v-card-title>Eliminar Curso</v-card-title>
                    <v-card-text>¿Estas seguro de eliminar el curso?</v-card-text>
                    <v-card-actions>
                        <v-btn color="red" text @click="deleteCursoConfirm(idToDelete)">Eliminar</v-btn>
                        <v-btn @click="dialogDelete=false">Cancelar</v-btn>
                    </v-card-actions>
                </v-card>
               </template>
            </v-dialog>
        </div>
        <v-row v-for="alert in alerts" :key="alert.color">
            <tabla-alert :alert="alert"/>
        </v-row>
        <div>
           
        </div>
    </div>
</template>

<script>
import TablaCursos from '@/components/TablaCursos.vue';
import TablaAlert from '@/components/TablaAlert.vue';
import AgregaCursoForm from '@/components/AgregaCursoForm.vue';
import EditarCurso from '@/components/EditarCurso.vue';
import { mapState,mapGetters,mapActions } from 'vuex';
export default {
    name: 'Admin-View',
    // props: {},
    data: function(){
        return {
            dialog:false,
            dialogDelete:false,
            isActive:false,
            showEdit:false,
            idEdit: null,
            CursoTitle:null,
            idToDelete:null
        }
    },
    computed: {
        ...mapState(['cursos']),
        ...mapGetters(['alumnosPermitidos']),
        ...mapGetters(['alumnosInscritos']),
        ...mapGetters(['cursosTerminados']),
        ...mapGetters(['totalCursos']),

        cuposRestantes(){
            return this.alumnosPermitidos - this.alumnosInscritos
        },
        cursosActivos(){
            return this.totalCursos - this.cursosTerminados
        },

        alerts(){
            return[
                {
                    color: 'purple',
                    icon: 'mdi-account-multiple',
                    title: `cantidad total de alumnos Permitidos: ${this.alumnosPermitidos} alumnos.`,
                },
                {
                    color: 'blue',
                    icon: 'mdi-account-check',
                    title: `Cantidada total de alumnos inscritos: ${this.alumnosInscritos} alumnos.`
                },
                {
                    color: 'red',
                    icon: 'mdi-account-plus',
                    title: `Cantidad total de cupos restantes: ${this.cuposRestantes} alumnos.`
                },
                {
                    color: 'purple-accent-3',
                    icon: 'mdi-cancel',
                    title: `Cantidad de cursos terminados: ${this.cursosTerminados} cursos.`
                },
                {
                    color:'light-green-darken-2',
                    icon:'mdi-bell-ring-outline',
                    title: `Cantidad total de cursos activos: ${this.cursosActivos} cursos.`
                },
                {
                    color: 'orange',
                    icon: 'mdi-bell-ring-outline',
                    title: `Cantidad total de cursos: ${this.totalCursos} cursos.`
                }
            ]
        }
        
    },
    methods: {
        openDialog(){
            this.dialog=true
            this.CursoTitle='Agregar Curso'
        },
        ...mapActions(['addCurso','removeCurso','editarCursoConfirm']),

        crearCurso(newCurso){
            this.CursoTitle=null
            this.dialog=false
            this.addCurso(newCurso)
        },
        deleteCurso(id){
            this.dialogDelete=true
            this.idToDelete=id;
            
        },
        deleteCursoConfirm(id){
            this.removeCurso(id);
            this.dialogDelete=false;
        },
        cerrarFormulario(){
            this.dialog=false
            this.showEdit=false
            this.idEdit=null
            this.CursoTitle=null
        },
        editarCurso(id){
            this.CursoTitle='Editar Curso'
            this.showEdit = true
            this.idEdit = id
            this.dialog=true
            // console.log(this.cursos.find((curso)=>curso.id==id))
        },
        editarCursoById(curso){
            this.editarCursoConfirm(curso)
            this.dialog=false
            this.idEdit=false
            this.CursoTitle=null
        }
    },
    // watch: {},
    components: {
        'tabla-cursos':TablaCursos,
        'tabla-alert': TablaAlert,
        'form-agregar-curso': AgregaCursoForm,
        'editar-curso': EditarCurso
    },
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    created(){

    }
    // -- End Lifecycle Methods
}
</script>

<style scoped>
    
</style>