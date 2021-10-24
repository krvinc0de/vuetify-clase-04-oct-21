<template>
<div>
  <Header texto="Mis datos"/>
  <div class="contenido">
    <Datos/>
  </div>
</div>
</template>

<script>
import Header from '@/components/Header.vue'
import Datos from '@/components/Datos.vue'
  export default {
    name: 'Home',
    components: {
      Header,
      Datos
    }
  }
</script>

<style scoped>
.contenido{
  min-height: calc(100vh - 80px - 70px);
  display: flex;
  justify-content: center;
  align-items: center;
}
.card{
  padding-top: 10px;
}
</style>