<template>
    <v-app-bar color="#6A1B9A">
      <v-row flex justify="space-around" align="center">
        <v-app-bar-nav-icon variant="text" class="text-white" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        <h1 class="text-white">Cursos AlfaWeb</h1>
        <div class="d-flex">
          <div class="mr-4">
          <v-btn variant="tonal" to="/"><v-icon size="30" class="text-white">mdi-home</v-icon></v-btn>
          </div>
          <div>
            <v-btn variant="tonal" to="/admin" class="pr-4"><v-icon size="30" class="text-white">mdi-wrench</v-icon></v-btn>
          </div>
        </div>
      </v-row>
    </v-app-bar>
</template>

<script>
export default {
    name: 'nav-bar-comp',
    // props: {},
    data: function(){
        return {}
    },
    // computed: {},
    // methods: {},
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