<template>
  <div class="contenido">
    <div class="card">
    <v-hover>
    <template v-slot:default="{ hover }">
      <v-card
        class="mx-auto"
        max-width="344"
      >
        <v-img src="https://cdn.vuetifyjs.com/images/cards/forest-art.jpg"></v-img>

        <v-card-text>
          <h2 class="text-h6 primary--text">
            titulo
          </h2>
          texto
        </v-card-text>
        <v-fade-transition>
          <v-overlay
            v-if="hover"
            absolute
            color="#036358"
          >
            <v-btn>Muestrame mas</v-btn>
          </v-overlay>
        </v-fade-transition>
      </v-card>
    </template>
  </v-hover>
  </div>
    <div class="card">
    <v-hover>
    <template v-slot:default="{ hover }">
      <v-card
        class="mx-auto"
        max-width="344"
      >
        <v-img src="https://cdn.vuetifyjs.com/images/cards/forest-art.jpg"></v-img>

        <v-card-text>
          <h2 class="text-h6 primary--text">
            titulo
          </h2>
          texto
        </v-card-text>
        <v-fade-transition>
          <v-overlay
            v-if="hover"
            absolute
            color="#036358"
          >
            <v-btn>Muestrame mas</v-btn>
          </v-overlay>
        </v-fade-transition>
      </v-card>
    </template>
  </v-hover>
  </div>    <div class="card">
    <v-hover>
    <template v-slot:default="{ hover }">
      <v-card
        class="mx-auto"
        max-width="344"
      >
        <v-img src="https://cdn.vuetifyjs.com/images/cards/forest-art.jpg"></v-img>

        <v-card-text>
          <h2 class="text-h6 primary--text">
            titulo
          </h2>
          texto
        </v-card-text>
        <v-fade-transition>
          <v-overlay
            v-if="hover"
            absolute
            color="#036358"
          >
            <v-btn>Muestrame mas</v-btn>
          </v-overlay>
        </v-fade-transition>
      </v-card>
    </template>
  </v-hover>
  </div>
  </div>
<template/>

<script>
  export default {
    data: () => ({
      overlay: false,
    })
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