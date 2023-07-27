<template>
  <div>
    <v-container>
      <v-row>
        <v-col cols="12" md="4" lg="4" v-for="curso in cursos" :key="curso.id">
          <card-cursos :curso="curso"/>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import CardCursos from '@/components/CardCursos.vue';
import { mapState } from 'vuex';
export default {
  name: 'Home-View',
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
    'card-cursos':CardCursos
  },
  // mixins: [],
  // filters: {},
  // -- Lifecycle Methods
  // -- End Lifecycle Methods
}
</script>

<style scoped>
  
</style>