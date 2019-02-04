<template>
  <v-layout>
    <v-flex text-xs-center>
      <div v-if="vehicle">
        <h1>{{ vehicle.vehicleDetails.year }} {{ vehicle.vehicleDetails.make }} {{ vehicle.vehicleDetails.model }}</h1>
        <div class="image-container">
          <v-img
            :src="vehicle.vehicleDetails.image.hero.md"
            :alt="`${vehicle.vehicleDetails.year } ${ vehicle.vehicleDetails.make } ${ vehicle.vehicleDetails.model} `"
            aspect-ratio="1.7"
            class="image"
          />
        </div>

        <v-layout justify-center>
          <v-btn
            color="info"
            dark
            nuxt
            to="/"
          >
            Back to List
          </v-btn>
        </v-layout>
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
import vehicle from '~/apollo/queries/vehicle'

export default {
  apollo: {
    vehicle: {
      query: vehicle,
      prefetch: ({ route }) => ({ id: route.params.id }),
      variables() {
        return { id: this.$route.params.id }
      }
    }
  }
}
</script>

<style scoped>
.image-container {
  max-width: 600px;
  margin: 0 auto 2rem;
}
</style>
