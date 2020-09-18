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
        <h1>Welcom to {{ title }} Page</h1>
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
      title: 'Blog'
    }
  }
}
</script>
