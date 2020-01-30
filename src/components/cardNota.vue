<template>
    <v-card
        color="#385F73"
        >
        <v-card-title class="headline">{{nota.titulo}}</v-card-title>
        <v-card-text> {{nota.descrição}} </v-card-text>

        <v-card-actions class='justify-end'>
            <v-tooltip bottom>
            <template v-slot:activator= '{on}'>
                <v-btn icon v-on ='on' @click="$emit('clickEditNota', id)" color='white'>
                <v-icon>mdi-pencil</v-icon>
                </v-btn>
            </template>
            <span>Editar</span>
            </v-tooltip>
            <v-tooltip bottom>
            <template v-slot:activator= '{on}'>
                <v-btn icon v-on ='on' @click="$emit('clickRemoveNota', id)" color='white'>
                <v-icon>mdi-delete</v-icon>
                </v-btn>
            </template>
            <span>Apagar</span>
            </v-tooltip>
        </v-card-actions>
    </v-card>
</template>
<script>

export default {
  name: 'cardName',
  props: {
    id: Number,
    nota: Object
  }
}
</script>
