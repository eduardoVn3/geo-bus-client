<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      fixed
      app
    >
      <v-list dense>
        <v-list-tile v-for="(itemMenu, key) in itemsMenu" v-bind="key" @click="nextPage(itemMenu.path)">
          <v-list-tile-action>
            <v-icon>$vuetify.icons.{{itemMenu.icon}}</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>{{itemMenu.name}}</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar color="primary" fixed app>
      <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title class="headline text-uppercase">
        <span>GeoBus</span>
        <!-- <span class="font-weight-light">MATERIAL DESIGN</span> -->
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <!-- <v-btn
        flat
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>fas fa-external-link-alt</v-icon>
      </v-btn> -->
    </v-toolbar>

    <v-content>
      <v-container fluid>
         <router-view/>
      </v-container>
    </v-content>
    <v-footer color="primary" app>
      <span class="white--text">&copy; GeoBus 2018</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  components: {
  },
  data () {
    return {
      drawer: null,
      itemsMenu: [
        { name: 'Home', icon: 'home', path: 'Home' },
        { name: 'Lista de unidades', icon: 'home', path: 'lista' }
      ]
    }
  },
  methods: {
    nextPage (path) {
      console.log(path)
      this.$router.replace(path)
    }
  }
}
</script>
