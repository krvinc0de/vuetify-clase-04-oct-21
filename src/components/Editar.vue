<template>
    <div class="pa-2 ma-2">
        <div class="text-h4">
            Template editar
            <v-btn onclick="window.location.href='listar'">
              prueba
            </v-btn>
        </div>
        <v-form
            ref="form"
            v-model="valid"
            lazy-validation
            class="pa-10 border-10"
        >
            <v-text-field
            v-model="name"
            :counter="10"
            :rules="nameRules"
            label="Name"
            required
            ></v-text-field>

            <v-text-field
            v-model="email"
            :rules="emailRules"
            label="E-mail"
            required
            ></v-text-field>

            <v-btn
            color="success"
            class="mr-4"
            @click="modificarUsuario"
            >
            <v-icon left>
                mdi-content-save
            </v-icon>
            Editar usuario
            </v-btn>

            <v-btn
            color="error"
            class="mr-4"
            @click="goHome()"
            >
            <v-icon left>
                mdi-eraser-variant
            </v-icon>
                Regresar
            </v-btn>

        </v-form>
    </div>
</template>

<script>
  export default {
    data: () => ({
      valid: true,
      name: '',
      nameRules: [
        v => !!v || 'Name is required',
        v => (v && v.length <= 10) || 'Name must be less than 10 characters',
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
      usuario: {}

    }),

    methods: {
      goHome () {
        window.location.href="listar"
      },
      modificarUsuario () {
        
      },
      obtenerUsuario(){
          console.log(this.idUsuario)
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