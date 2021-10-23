<template>
  <div>
    <div>
      <Header texto="Editar usuario"/>
    </div>
    <div class="contenido">
        <div class=" titulo text-center">
            <h1 class="text-h4 font-weight-thin mb-4 texto">
              Atencion
            </h1>
            <p class="subheading texto">
              Si editas un usuario este se modificara en la base de datos
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
                v-model="usuario.nombre"
                :counter="70"
                :rules="nameRules"
                label="Nombre"
                required
                ></v-text-field>

                <v-text-field
                v-model="usuario.correo"
                :rules="emailRules"
                label="Correo electronico"
                required
                ></v-text-field>
              </div>
                <div class="text-center botones">
                <v-btn
                color="success"
                class="mr-4"
                @click="modificarUsuario()"
                >
                <v-icon left>
                    mdi-account-edit
                </v-icon>
                Editar usuario
                </v-btn>

                <v-btn
                color="error"
                class="mr-4"
                @click="goList()"
                >
                <v-icon left>
                    mdi-arrow-left-circle
                </v-icon>
                    Regresar
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
                  <v-card-title class="text-h6">
                  Usuario Registrado
                </v-card-title>
                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn
                    color="red darken-1"
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
      dialog: false,
      valid: true,
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
      usuario: []

    }),

    methods: {
      goList () {
        window.location.href="listar"
      },
      modificarUsuario () {
            let that = this
            fetch('http://localhost/?actualizar='+that.usuario.id,{
                method:"POST",
                body: JSON.stringify(that.usuario)
            })
            .then( respuesta => respuesta.json())
            .then ((datos => {
                console.log(datos)
                this.dialog = true
            }))
      },
      obtenerUsuario(){
          console.log(this.idUsuario)
          fetch('http://localhost/?consultar='+this.idUsuario)
          .then( respuesta => respuesta.json())
          .then((datos) =>{
                this.usuario = datos[0]
                console.log('usuario', this.usuario.id)
            })
      }
    },
    mounted() {
        this.obtenerUsuario()
    },
    computed:{
        idUsuario: {
            get(){
                return this.$store.state.idUsuario
            }
        }
    }
  }
</script>

<style scoped>
.titulo{
  padding-top: 20px;
  padding-bottom: 10px
}
.botones{
  padding-top: 20px;
}
.contenido{
  min-height: calc(100vh - 80px - 70px);
}
.entrada{
  padding-left: 10%;
  width: 90%;
}
</style>