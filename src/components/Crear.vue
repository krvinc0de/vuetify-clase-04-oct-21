<template>
<div class="pa-2 ma-2">
    <div class="text-h4 text-center pa-2">
        Usuarios del sistema
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
      @click="guardar"
    >
      <v-icon left>
          mdi-content-save
      </v-icon>
      Guardar
    </v-btn>

    <v-btn
      color="error"
      class="mr-4"
      @click="reset"
    >
      <v-icon left>
          mdi-eraser-variant
      </v-icon>
        Reiniciar datos
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
            window.location.href = 'listar'
        }))
      },
      reset () {
        this.$refs.form.reset()
      }
    },
  }
</script>