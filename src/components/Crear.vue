<template>
<div>
  <Header texto="Registrar usuario"/>
  <div class="contenido">
        <div class=" titulo text-center">
            <h1 class="text-h4 font-weight-thin mb-4 texto">
              Atencion
            </h1>
            <p class="subheading texto">
              Estas apunto de agregar un usuario a la base de datos
            </p>
        </div>
          <div class="pa-2 ma-2">
            <v-form
                ref="form"
                v-model="valid"
                lazy-validation
                class="pa-10 border-10"
            >
              <div class="entrada">
                <v-text-field
                v-model="name"
                :counter="70"
                :rules="nameRules"
                label="Nombre"
                required
                ></v-text-field>

                <v-text-field
                v-model="email"
                :rules="emailRules"
                label="Correo electronico"
                required
                ></v-text-field>
              </div>
                <div class="text-center botones">
                <v-btn
                color="success"
                class="mr-4"
                @click="guardar()"
                >
                <v-icon left>
                    mdi-content-save
                </v-icon>
                Registrar usuario
                </v-btn>

                <v-btn
                color="error"
                class="mr-4"
                @click="reset()"
                >
                <v-icon left>
                    mdi-eraser-variant
                </v-icon>
                    Cancelar
                </v-btn>
                </div>
            </v-form>
            <v-dialog
              v-model="dialog"
              persistent
              max-width="290"
            >
              <v-card>
                <v-icon
                  icon="mdi-lock"
                  color="white"
                >
                  mdi-lock
                </v-icon>
                  <v-card-title class="text-h5">
                  ¡Usuario Registrado!
                </v-card-title>
                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn
                    color="green darken-1"
                    text
                    @click="dialog = false"
                  >
                    Continuar
                  </v-btn>
                  <v-spacer></v-spacer>
                  <v-btn
                    color="green darken-1"
                    text
                    onclick="window.location.href='listar'"
                  >
                    Ir a lista
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
      </div>
  </div>
</div>
</template>

<script>
import Header from '@/components/Header.vue'
  export default {
    components:{
      Header
    },
    data: () => ({
      valid: true,
      dialog: false,
      name: '',
      nameRules: [
        v => !!v || 'Name is required',
        v => (v && v.length <= 70) || 'Name must be less than 10 characters',
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
      usuario: {}

    }),

    methods: {
      guardar () {
        var datosUsuario = {
            nombre: this.name,
            correo: this.email
        }
        console.log(datosUsuario)
        fetch('http://localhost/?insertar=1', {
            method: "POST",
            body: JSON.stringify(datosUsuario) //texto plano
        })
        .then(respuesta => respuesta.json())
        .then((datosRespuesta =>{
            console.log(datosRespuesta)
            this.reset()
            this.dialog = true
        }))
      },
      reset () {
        this.$refs.form.reset()
      }
    },
  }
</script>

<style scoped>
.contenido{
  min-height: calc(100vh - 80px - 70px);
}
.titulo{
  padding-top: 20px;
  padding-bottom: 10px
}
.entrada{
  padding-left: 10%;
  width: 90%;
}
</style>