<template>
  <v-footer
    dark
    padless
  >
    <v-card
      flat
      tile
      class="indigo lighten-1 white--text text-center"
    >
      <v-card-text>
        <v-btn
          v-for="icon in icons"
          :key="icon"
          class="mx-4 white--text"
          icon
        >
          <v-icon size="24px">
            {{ icon }}
          </v-icon>
        </v-btn>
      </v-card-text>

      <v-card-text class="white--text -center pt-0">
        <strong> Rejoins-nous sur les réseaux sociaux, et partage ton ressenti, tes dernières découvertes.</strong>
        <div> Culture-Map est avant tout un outil de partage. L'objectif principale de Culture-Map est d'offrir une alternative à la découverte d'espaces culturels.
        La Culture comme passion, loisir, gratuite et facile d'accès pour tous.</div>
        <div> Pour l'amour de la connaissance et de l'art.</div>
      </v-card-text>

      <v-divider></v-divider>

      <v-card-text class="white--text">
        {{ new Date().getFullYear() }} — <strong>Culture-Map</strong>
      </v-card-text>
    </v-card>
  </v-footer>
</template>

<script>
  export default {
    name: 'HomeFooter',
        data: () => ({
      icons: [
        'mdi-facebook',
        'mdi-twitter',
        'mdi-linkedin',
        'mdi-instagram',
      ],
    }),
  }
</script>

<style scoped>

</style>