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
      <div class="text-center">
        <h2>Welcome to {{ title }} Page</h2>
        <h2>This Page is not finished yet</h2>
      </div>
    </v-flex>
  </v-layout>
</template>

<style scoped>
</style>

<script>
export default {
  data () {
    return {
      title: 'About'
    }
  }
}
</script>
