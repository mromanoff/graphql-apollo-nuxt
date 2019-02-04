<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm8
      md6
    >
      <v-card class="card" v-for="vehicle in vehicles" :key="vehicle.id">
        <v-img
          :src="vehicle.vehicleDetails.image.hero.md"
          :alt="`${vehicle.vehicleDetails.year } ${ vehicle.vehicleDetails.make } ${ vehicle.vehicleDetails.model} `"
          aspect-ratio="1.7"
        ></v-img>


        <v-card-title class="headline">
          {{ vehicle.vehicleDetails.year }} {{ vehicle.vehicleDetails.make }} {{ vehicle.vehicleDetails.model }}
        </v-card-title>
        <v-card-text>
          <p>
            Bacon ipsum dolor sit amet salami jowl corned beef, andouille flank tongue ball tip kielbasa pastrami tri-tip meatloaf short loin beef biltong. Cow bresaola ground round strip steak fatback meatball shoulder leberkas pastrami sausage corned beef t-bone pork belly drumstick.
          </p>
        </v-card-text>
        <v-card-actions>
          <v-layout justify-center>
            <v-btn
              color="info"
              dark
              nuxt
              :to="`/report/${vehicle.id}`"
            >
              Continue
            </v-btn>
          </v-layout>
        </v-card-actions>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
import vehicles from '~/apollo/queries/vehicles.gql'

export default {
  apollo: {
    vehicles: {
      prefetch: true,
      query: vehicles
    }
  }
}
</script>

<style scoped>
.card {
  margin-bottom: 1rem;
  max-width: 500px;
  padding-bottom: 1rem;
}

.card__image {
  width: 200px;
  height: auto;
}
</style>
