<template>
  <div>
    <Header texto="Mis datos"/>

  </div>
</template>

<script>
import Header from '@/components/Header.vue'
  export default {
    data: () => ({
      overlay: false,
    }),
    name: 'Home',
    components: {
      Header
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
<style/>