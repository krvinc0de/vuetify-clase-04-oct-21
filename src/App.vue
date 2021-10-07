<template>
  <v-app>
    <Navegacion/>
    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>
import Navegacion from'@/components/Navegacion.vue'
export default {
  name: 'App',
  components:{
    Navegacion
  },
  data: () => ({
    //
  }),
};
</script>
