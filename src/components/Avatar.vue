<template>
  <q-avatar :color="color" text-color="white">
    {{ avatarLetter }}
    <q-tooltip> {{ firstName }} {{ lastName }} </q-tooltip>
  </q-avatar>
</template>

<script lang="ts">
import Vue from 'vue'

const bgColors = [
  'primary',
  'secodary',
  'accent',
  'dark',
  'positive',
  'negative'
]

export default Vue.component('c-avatar', {
  props: {
    firstName: {
      type: String,
      required: true
    },

    lastName: {
      type: String,
      required: true
    },

    imageData: {
      type: String
    }
  },

  computed: {
    avatarLetter() {
      return this.lastName?.charAt(0)?.toUpperCase() || 'X'
    },

    color() {
      const charCode =
        this.lastName
          ?.charAt(0)
          ?.toUpperCase()
          ?.charCodeAt(0) || 0

      const colorIndex = charCode % bgColors.length

      return bgColors[colorIndex]
    }
  }
})
</script>

<style lang="scss"></style>
