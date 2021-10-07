<template>
    <div class="pa-2 ma-2">
        <div class="text-h4">
            Usuarios del sistema
        </div>
    </div>
</template>

<script>
export default {
    created: function(){

    },
    methods: {
        consultarUsuarios(){
            //sirve para ir a links en servidores web fetch
            fetch('http://localhost/usuarios/')
            .then(respuesta => respuesta.json())
            .then( (datos) => {
                console.log(datos)
            })
            .catch(console.log)
        }
    }
}
</script>