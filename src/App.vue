<template>
  <v-app>
    <v-app-bar
      app
      dark
      color="pink"
    >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>Teste</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
    </v-app-bar>
    <v-content>
      <listaNomes/>

    </v-content>

  </v-app>
</template>

<script>
import listaNomes from './components/listaNomes'

export default {
  name: 'App',

  components: {
    listaNomes
  },

  data: () => ({
    //
  })
}
</script>
