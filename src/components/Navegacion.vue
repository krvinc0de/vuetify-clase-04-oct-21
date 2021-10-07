<template>
  <v-card>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant.sync="mini"
      permanent
      app
      dark
      expand-on-hover
    >
      <v-list-item class="px-2">
        <v-list-item-avatar>
          <v-img src="https://randomuser.me/api/portraits/men/85.jpg"></v-img>
        </v-list-item-avatar>

        <v-list-item-title>Kevin M.</v-list-item-title>

        <v-btn
          icon
          @click.stop="mini = !mini"
        >
          <v-icon>mdi-chevron-left</v-icon>
        </v-btn>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense>
        <v-list-item
          v-for="item in items"
          :key="item.title"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <router-link class="link" :to="`${item.path}`">{{item.title}}</router-link>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </v-card>
</template>

<script>
  export default {
    data () {
      return {
        drawer: true,
        items: [
          { title: 'Inicio', icon: 'mdi-home-city', path: '/' },
          { title: 'Listar', icon: 'mdi-format-list-checkbox', path: '/Listar' },
          { title: 'Crear', icon: 'mdi-account-edit-outline', path: '/Crear' },
          { title: 'Editar', icon: 'mdi-account-group-outline', path: '/Editar' },
        ],
        mini: true,
      }
    },
  }
</script>

<style scoped>
.link{
  text-decoration: none;
  color: white;
}
</style>