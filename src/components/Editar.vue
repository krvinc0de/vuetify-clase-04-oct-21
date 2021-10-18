<template>
    <div class="pa-2 ma-2">
        <div class="text-h4">
            Template editar
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
    
}
</script>