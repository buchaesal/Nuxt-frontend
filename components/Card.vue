<template>
  <v-card
    class="mx-auto"
    max-width="344"
  >
    <v-img
      src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
      height="200px"
    ></v-img>

    <v-card-title>
      {{ product.pdName }}
    </v-card-title>
  </v-card>
</template>

<script>
export default {
  name: "Card",
  props: ['product']
}
</script>

<style scoped>

</style>
