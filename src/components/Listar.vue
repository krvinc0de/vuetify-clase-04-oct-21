<template>
  <div>
    <div>
      <Header texto="Usuarios registrados"/>
    </div>
    <div class="contenido">
    <div class="pa-4">
        <div>
            <v-data-table 
            :headers="encabezados"
            :items="usuarioDB"
            :items-per-page="5"
            class="elevation-10"
            >
              <template #[`item.editar`]="{ item }">
                <v-btn color="deep-purple lighten-3" small @click="editarUsuario(item.id)">
                  <v-icon>
                    mdi-account-edit
                  </v-icon>
                </v-btn>
              </template>
              <template #[`item.borrar`]="{ item }">
                <v-btn color="red lighten-1" small @click="guardarUsuario(item.id)">
                  <v-icon>
                    mdi-delete
                  </v-icon>
                </v-btn>
              </template>
            </v-data-table>
            <v-dialog
              v-model="dialog"
              persistent
              max-width="290"
            >
              <v-card>
                <v-card-title class="text-h5">
                  Atencion!!
                </v-card-title>
                <v-card-text>Si eliminas un usuario no podras recuperar la informacion del usuario eliminado.</v-card-text>
                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn
                    color="red darken-1"
                    text
                    @click="dialog = false"
                  >
                    Cancelar
                  </v-btn>
                  <v-btn
                    color="green darken-1"
                    text
                    @click="borrarUsuario(usuarioId)"
                  >
                    Eliminar
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
        </div>
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
    data() {
        return {
            usuarioDB: [],
            encabezados:[
                {text: 'ID', value: 'id', sortable: false},
                {text: 'Nombre', value: 'nombre', sortable: false},
                {text: 'Correo', value: 'correo', sortable: false},
                {text: 'Editar', value: 'editar', sortable: false},
                {text: 'Borrar', value: 'borrar', sortable: false}
            ],
            dialog: false
        }
    },
    created: function(){
        this.consultarUsuarios()
    },
    methods: {
        consultarUsuarios(){
            //sirve para ir a links en servidores web fetch
            fetch('http://localhost/')
            .then(respuesta => respuesta.json())
            .then((datosRespuesta) =>{
                this.usuarioDB = []
                if (typeof datosRespuesta[0].success === 'undefined') {
                    this.usuarioDB = datosRespuesta
                    //recorre el array de la variable pero en el proyecto ni sirve JAJAJAJAJA
                    this.usuarioDB.forEach(item =>{
                        console.log(item)
                    })
                    //console.log(this.usuarioDB)
                }
            })
            //muestra los datos en la consola
            .then( (datos) => {
                console.log(datos)
            })
            .catch(console.log)
        },
        editarUsuario(id){
          //console.log(usuario)
          this.$store.commit('setIdUsuario', id)
          window.location.href="editar"
        },
        borrarUsuario(usuarioId){
          console.log(usuarioId)
          fetch('http://localhost/?borrar='+usuarioId)
          .then(respuesta => respuesta.json)
          .then((datosRespuesta)=>{
            this.usuarioId = null
            window.location.href="listar"
          })
        },
        guardarUsuario(id){
          this.usuarioId = id
          this.dialog = true
        }
    }
}
</script>

<style scoped>
.contenido{
  min-height: calc(100vh - 80px - 70px);
}
</style>