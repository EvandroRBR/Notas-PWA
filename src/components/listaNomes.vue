<template>
    <v-container fluid>
      <v-row>
        <v-col v-for="(nota, index) in notas" :key="index" cols="12" md='4'>
          <cardNota :nota="nota" :id="index"
          @clickEditNota='editarNota'
          @clickRemoveNota='removerNota'
          ></cardNota>
        </v-col>

      </v-row>
      <v-btn
      fixed
      dark
      fab
      bottom
      right
      color='pink'
      @click='dialog=true'>
        <v-icon>mdi-plus</v-icon>
      </v-btn>
      <v-dialog v-model="dialog" fullscreen hide-overlay transition="dialog-bottom-transition">
        <v-card>
        <v-toolbar dark color="primary">
          <v-btn icon dark @click="dialog = false">
            <v-icon>mdi-close</v-icon>
          </v-btn>
          <v-toolbar-title>Settings</v-toolbar-title>
          <v-spacer></v-spacer>
          <v-toolbar-items>
            <v-btn dark text @click="salvarNota">Save</v-btn>
          </v-toolbar-items>
        </v-toolbar>
          <v-form>
            <v-container>
              <v-row>
                <v-col cols="12">
                  <v-text-field
                  label="titulo"
                  v-model="nota.titulo">
                  </v-text-field>
                </v-col>
                <v-col cols="12">
                  <v-textarea label="descrição"
                  aria-placeholder="comprar pão de queijo!"
                  v-model="nota.descrição">
                  </v-textarea>
                </v-col>
              </v-row>
            </v-container>
          </v-form>
        </v-card>

      </v-dialog>
    </v-container>
</template>
<script>

import cardNota from './cardNota.vue'

export default {
  name: 'listaNomes',
  components: {
    cardNota
  },
  data () {
    return {
      dialog: false,
      nota: {
        texto: null,
        descrição: null
      },
      notas: []
    }
  },
  methods: {
    salvarNota () {
      let nota = {}
      nota = Object.assign(nota, this.nota)
      if (nota.id !== null && nota.id >= 0) {
        this.notas[nota.id] = nota
      } else {
        this.notas.push(nota)
      }
      this.dialog = false
      this.limpaNota()
    },
    limpaNota () {
      for (let k in this.nota) {
        this.nota[k] = null
      }
    },
    editarNota (id) {
      this.nota = this.notas[id]
      this.nota.id = id
      this.dialog = true
    },
    removerNota (id) {
      this.notas.splice(id, 1)
    }
  }
}

</script>
