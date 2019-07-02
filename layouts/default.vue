<template>
  <v-app dark>
    <nuxt/>
  </v-app>
</template>

<script>
  export default {
    data() {
      return {
        clipped: false,
        drawer: false,
        fixed: false,
        items: [],
        miniVariant: false,
        right: true,
        rightDrawer: false,
        title: 'Access violation at 0x00000000'
      }
    },
    head() {
      return {
        title: this.title,
        meta: [
          // hid is used as unique identifier. Do not use `vmid` for it as it will not work
          {hid: 'description', name: 'description', content: 'A personal website'}
        ]
      }
    }
  }
</script>

<style>
</style>
