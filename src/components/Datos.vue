<template>
  <div class="contenido">
    <div>
        <v-hover>
    <template v-slot:default="{ hover }">
      <v-card
        class="mx-auto"
        max-width="344"
      >
        <v-img src="../assets/perfil.jpg"></v-img>

        <v-card-text>
          <h2 class="text-h6 primary--text">
            Sobre mi
          </h2>
          Informacion sobre el creador del proyecto
        </v-card-text>
        <v-fade-transition>
          <v-overlay
            v-if="hover"
            absolute
            color="#036358"
          >
            <v-btn @click="kevin()">Muestrame mas</v-btn>
          </v-overlay>
        </v-fade-transition>
      </v-card>
    </template>
  </v-hover>
    </div>  | |
    <div>
        <v-hover>
    <template v-slot:default="{ hover }">
      <v-card
        class="mx-auto"
        max-width="344"
      >
        <v-img src="../assets/uts.jpg"></v-img>

        <v-card-text>
          <h2 class="text-h6 primary--text">
            Universidad
          </h2>
          Universidad Tecnologica de Salamanca
        </v-card-text>
        <v-fade-transition>
          <v-overlay
            v-if="hover"
            absolute
            color="#036358"
          >
            <v-btn href="http://www.utsalamanca.edu.mx/" target="_blank">Muestrame mas</v-btn>
          </v-overlay>
        </v-fade-transition>
      </v-card>
    </template>
  </v-hover>
    </div>
      | |
    <div>
        <v-hover>
    <template v-slot:default="{ hover }">
      <v-card
        class="mx-auto"
        max-width="344"
      >
        <v-img src="../assets/carrera.jpg"></v-img>

        <v-card-text>
          <h2 class="text-h6 primary--text">
            Carrera
          </h2>
          TIS: Area Dessarrollo de software
        </v-card-text>
        <v-fade-transition>
          <v-overlay
            v-if="hover"
            absolute
            color="#036358"
          >
            <v-btn href="http://www.utsalamanca.edu.mx/tsutis" target="_blank">Muestrame mas</v-btn>
          </v-overlay>
        </v-fade-transition>
      </v-card>
    </template>
  </v-hover>

  <!-- Tarjetas de informacion -->
  <v-dialog 
  v-model="dialog"
  persistent
  >
  <v-card
    :loading="loading"
    class="mx-auto my-12"
    max-width="380"
  >
    <template slot="progress">
      <v-progress-linear
        color="deep-purple"
        height="10"
        indeterminate
      ></v-progress-linear>
    </template>

    <v-img
      height="250"
      src="../assets/perfil.jpg"
    ></v-img>
    <v-card-title>Kevin Oswaldo Velazquez Medina</v-card-title>
    <v-card-text>
      <div>Estoy aprendiendo programacion</div>
    </v-card-text>

    <v-divider class="mx-4"></v-divider>

    <v-card-title>Mis intereses</v-card-title>

    <v-card-text>
      <v-chip-group>
        <v-chip>Programacion</v-chip>

        <v-chip>Github</v-chip>

        <v-chip>Arte</v-chip>

        <v-chip>Musica</v-chip>
      </v-chip-group>
    </v-card-text>

    <v-card-actions>
      <v-btn
        color="deep-purple lighten-2"
        text
        @click="dialog=false"
      >
        Cerrar
      </v-btn>
    </v-card-actions>
  </v-card>

  </v-dialog>


    </div>
  </div>
</template>

<script>
  export default {
    data: () => ({
      dialog: false,
      selection: true,
      overlay: false,
    }),
    methods:{
      kevin(){
        this.dialog = true
      }
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